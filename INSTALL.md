# Installing VERUS Free 0.1.0

From an empty machine to the year your plant missed, with this page alone. VERUS Free is the data health check, a
headline board per plant for one company, and the year you missed: every problem VERUS would have caught in the last
twelve months, ranked by what it cost. It is free, with no time limit, under the terms in `TERMS.md`.

If you would rather not do this yourself, we set it up with your IT team, free: contact@resonanceinstitutellc.com.

## What is in this folder

- `start.sh`: one command to load, start and say where to sign in.
- `verus-free-0.1.0.tar`: VERUS itself, as a Docker image. Nothing else is downloaded except Docker's database
  image.
- `docker-compose.yml`: the three containers (its database, the screens with the API, and a worker).
- `it-request.md`: a page to forward to IT as it is.
- `read-only-logins.md`: the exact read-only login script for each kind of database.
- `downtime_log.csv`: a template, for an ERP that keeps no downtime.
- `TERMS.md`: the terms VERUS Free is used under.
- `THIRD_PARTY.md` and `THIRD_PARTY_LICENSES.txt`: the open-source libraries inside, and their licenses.

## What you need

- **A Linux machine**, recommended: a virtual machine with Ubuntu 22.04 or 24.04, 16 GB of memory, 4 CPUs and room
  for about twice the size of the ERP database, on the plant's own network, where it can reach the ERP's database.
- **Docker Engine with the Compose plugin**, free. The steps for Ubuntu are just below.
- **A read-only login** to the ERP's database, made by whoever looks after it (step 4).

To try it on a laptop instead, Docker Desktop on Windows or macOS works with 8 GB of memory. Docker Desktop is free
for personal use and for companies with fewer than 250 employees and under $10 million a year in revenue; larger
companies need a paid Docker subscription for it. Docker Engine on Linux has no such condition.

## Installing Docker on Ubuntu

Docker's own steps (docs.docker.com, "Install Docker Engine on Ubuntu"), as one block:

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl unzip
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo usermod -aG docker $USER
```

Sign out and back in, then `docker compose version` should print a version.

## Steps

1. **Unzip this folder on the machine and start VERUS**, inside it:
   ```bash
   sh start.sh
   ```
   The first time it loads VERUS (a minute or two). If port 8080 is taken it picks another. When VERUS answers it
   prints the address to open, the user name (`admin@verus.local`) and the first password.
2. **Sign in.** Open the address it printed. VERUS asks for a new password at once.

   *By hand instead, or on Windows or a Mac with Docker Desktop:* `docker load -i verus-free-0.1.0.tar`, then
   `docker compose up -d`; the first password is shown by `docker compose exec api cat /data/initial_admin_password`
   (on Windows, in PowerShell). Port 8080 taken: a file named `.env` here holding `VERUS_PORT=8090`.
3. **Connect the ERP.** Setup, Add source.
   - First create a read-only login for VERUS on the ERP's database, with the script in `read-only-logins.md`. The
     Setup screen then shows what the login can do, in plain words, and every statement VERUS will run: hand both to
     whoever approves database access.
   - Then press **Connect**. VERUS finds the tables, reads them, profiles them and maps them, one after another;
     Onboarding shows each stage. Where it is not sure, Review asks a few short questions, with a sample of your own
     rows.
   - Microsoft Dynamics AX 2012, Epicor Kinetic and Infor CloudSuite Industrial (SyteLine) are mapped with no AI
     model. Any other ERP needs one to work out its tables, once: copy `config/verus.example.yaml` to
     `config/verus.yaml`, put `ANTHROPIC_API_KEY=` and your key in `.env`, and run `sh start.sh` again. Its spend is
     capped in that file ($500 a month unless you lower it), and every call is counted on the Onboarding screen.
     Nothing else in VERUS Free uses a model.
4. **Run the year.** The year you missed, "Run the year". It reads a year of records: minutes on a small system, a
   few hours on a large one. You can leave the page while it works. When it is done, "Print the report" makes the
   page to hand to whoever signs.

**No downtime in your ERP?** Fill in `downtime_log.csv` (one row per stop: company, site, work center, start,
minutes, reason, planned Y or N), save it as `downtime_log` in a folder of its own, and add that folder as a source
(Setup, Add source, files). It maps itself, and the board's downtime tile fills in.

## What VERUS Free does not do

The screens that need licensed VERUS are in the menu with a lock and say what they do; their code is not in this
install. Licensed VERUS watches from today on: scrap and downtime every 15 minutes, a morning brief for each person,
agents of your own, action plans, dashboards, Ask. It is installed with you, and keeps everything VERUS Free has
found: www.verusops.com/pricing.

## Network

- **Inbound:** port 8080 (or yours), from the users' network only. Put your usual TLS in front of it.
- **Outbound while running:** nothing. No telemetry, no usage reporting, no update checks: VERUS never calls home.
- **To the ERP:** the database's own port, read only. VERUS cannot write to it: there is no code path for it.

Every VERUS process runs as an unprivileged user (uid 10001), never root. If you mount a folder for VERUS to read
files from, make it readable by uid 10001.

## Removing it

```bash
docker compose down -v
docker image rm verus-free:0.1.0
```

The machine is clean, and the ERP was never touched.
