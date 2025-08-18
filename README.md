# M365 Whitelist for Pi-hole

Curated allow and deny lists to keep Microsoft 365 services working (Outlook, Teams, SharePoint, OneDrive) while blocking telemetry noise.

This repo is for Enterprise/Worldwide tenants.
For GCC, see the fork here: [obiwantoby/O365Whitelist](https://github.com/obiwantoby/O365Whitlist).

 ## What it does

✅ Keeps M365 functional

✅ Blocks known telemetry endpoints

✅ Easy to apply, easy to roll back

 ## Quick Start

**1. Back up Pi-hole first (seriously):**
```
sudo cp /etc/pihole/gravity.db /etc/pihole/gravity.db.bak.$(date +%s)
```

**2. Clone:**
```
git clone https://github.com/TheSmashy/O365Whitelist.git
cd O365Whitelist
```

**3. Apply lists:**
```
python3 scripts/whitelist.py --env enterprise
pihole -g
pihole restartdns
```

**4. Roll back if you break Teams/Outlook:**
```
python3 scripts/uninstall.py
sudo cp /etc/pihole/gravity.db.bak.<timestamp> /etc/pihole/gravity.db
pihole -g
pihole restartdns
````
## Notes

Tested on Pi-hole v5. Works on v6 but you’ll likely add via Adlists instead of directly editing gravity.db.

Critical endpoints like login.microsoftonline.com are never denied. Don’t mess with them unless you want authentication loops.

Regex rules are optional — start with exact lists first.

## Credits

Original project: TheSmashy (this repo)

GCC fork: obiwantoby/O365Whitelist

## Disclaimer

This is community-maintained. Use at your own risk. Back up before applying.
