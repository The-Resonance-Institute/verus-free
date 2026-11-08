# VERUS Free

**Last year your plant lost money nobody saw. Find out how much. Free for 30 days.**

VERUS Free reads the last twelve months of your own ERP and shows you every problem it would have caught: the scrap
spikes, the customers slipping on delivery, the orders gone past due, the key account gone quiet. Each one ranked by
what it cost you, with the numbers behind it, and one page to print for whoever signs.

It runs on one machine inside your network and reads your ERP with a login that cannot write. None of your data
ever comes to us. Thirty days free, no card. **Get it at [www.verusops.com/free](https://www.verusops.com/free).**

## Get it

**On Windows** (any PC or server that can reach your ERP's database; no administrator rights, no Docker):

1. **Download** it from [www.verusops.com/free](https://www.verusops.com/free) (about 130 MB) and run it.
2. **Start menu, VERUS Free.** The first start takes a couple of minutes; then your browser opens VERUS and a box
   shows the first password. Then your work email and company start your 30 days.
3. **Connect your ERP** with a read-only login (Setup, Add source) and press **Connect**. Then **Run the year**.

**On Linux with Docker:** download the kit from [www.verusops.com/free](https://www.verusops.com/free) (about 540 MB),
unzip it and run `sh start.sh`. The guide is [INSTALL.md](INSTALL.md).

## What it needs

- A Windows PC or server (Windows 10, 11 or Server 2016 and later, 64-bit), 8 GB of memory or more, that can reach
  the ERP's database; or a Linux machine with Docker.
- A read-only login to the ERP's database. On SQL Server, Microsoft's ODBC Driver 17 or 18 for SQL Server on the
  Windows machine; most machines that reach SQL Server already have it.
- Microsoft Dynamics AX 2012, Epicor Kinetic and Infor CloudSuite Industrial (SyteLine) are mapped with no AI model.
  Any other ERP with a database needs a model key once, to work out its tables.

**Windows may warn** that it does not recognise the installer ("Windows protected your PC"): choose More info, then
Run anyway. The installer is not yet code-signed.

## What you get, free for 30 days

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

VERUS Free runs inside your network, and none of your data ever comes to us. To run the trial it sends us your work
email, company and a code made from the machine when you start it, then at most once a day the trial's identifier,
that code and the version. It cannot write to your ERP; there is no code path for it. The code that touches your database is open to read in
[VERUS Open](https://github.com/The-Resonance-Institute/verus-open).

## Terms

Free for 30 days for your own business under [TERMS.md](TERMS.md); after that it stops until you buy a license, and
everything you set up is kept. The open-source libraries inside are listed, with their
licenses, in the download (`THIRD_PARTY.md`, `THIRD_PARTY_LICENSES.txt`).

## Help

Rather have us set it up with your IT team? Free: [www.verusops.com/free](https://www.verusops.com/free) or
contact@resonanceinstitutellc.com.

VERUS is made by The Resonance Institute, LLC.
