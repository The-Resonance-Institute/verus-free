# VERUS Free

**Last year your plant lost money nobody saw. Find out how much. Free.**

VERUS Free reads the last twelve months of your own ERP and shows you every problem it would have caught: the scrap
spikes, the customers slipping on delivery, the orders gone past due, the key account gone quiet. Each one ranked by
what it cost you, with the numbers behind it, and one page to print for whoever signs.

It runs on one machine inside your network, reads your ERP with a login that cannot write, and sends nothing
anywhere. No form, no card, no time limit.

## Get it

1. **Download** [verus-free.zip](https://github.com/The-Resonance-Institute/verus-free/releases/latest/download/verus-free.zip)
   (about 540 MB) onto a Linux machine with Docker.
2. **Unzip it and run one command** in the folder:
   ```bash
   sh start.sh
   ```
   It loads VERUS, starts it, and prints the address to open and the first password.
3. **Connect your ERP** with a read-only login (the scripts are in the download) and press **Connect**. Then
   **Run the year**.

The full guide is [INSTALL.md](INSTALL.md), and it is in the download too, with a page to forward to IT.

## What it needs

- A Linux machine, recommended: Ubuntu 22.04 or 24.04, 16 GB of memory, 4 CPUs, on the plant's network where it can
  reach the ERP's database. Docker Desktop on Windows or macOS works to try it on a laptop.
- A read-only login to the ERP's database.
- Microsoft Dynamics AX 2012, Epicor Kinetic and Infor CloudSuite Industrial (SyteLine) are mapped with no AI model.
  Any other ERP with a database needs a model key once, to work out its tables.

## What you get, free, to keep

- **The year you missed:** every problem VERUS's starter agents would have raised in the last twelve months, ranked by
  dollars, with "Show the numbers" on each, and a printable report.
- **Your data health check:** where your own records mislead you, each with the query that proves it.
- **Your plant's board:** sales shipped, on time to the original promise, scrap and downtime, per plant.

## What it does not do

It looks back, once. Licensed VERUS watches from today on: scrap and downtime every 15 minutes, a morning brief for
each person, agents of your own, action plans, dashboards and Ask, and keeps everything VERUS Free found. Those
screens are in VERUS Free's menu with a lock; their code is not in the download.
[Pricing](https://www.verusops.com/pricing).

## Your data

VERUS Free runs inside your network. It never calls home: no telemetry, no usage reporting, no update checks. It
cannot write to your ERP; there is no code path for it. The code that touches your database is open to read in
[VERUS Open](https://github.com/The-Resonance-Institute/verus-open).

## Terms

Free to use for your own business under [TERMS.md](TERMS.md). The open-source libraries inside are listed, with their
licenses, in the download (`THIRD_PARTY.md`, `THIRD_PARTY_LICENSES.txt`).

## Help

Rather have us set it up with your IT team? Free: [www.verusops.com/free](https://www.verusops.com/free) or
contact@resonanceinstitutellc.com.

VERUS is made by The Resonance Institute, LLC.
