# Python Download

<https://www.python.org/downloads/>

The modern way is using the Python install manager.

## Python Manager (2026-02)

<https://www.python.org/downloads/release/pymanager-260/>:

```powershell
winget install 9NQ7512CXL7T
# installed Python Install Manager (command "py")

# then when you use "python3" or "python", it will prompt to install
# the latest Python version automatically via the manager
py --list          # list installed Python versions
py -3.12 script.py # run with a specific version
```

## Notes

- Use the newest version; if you run into a problem, try v3.7.
- Python v3.7.9 (2020-08-17) is the final bugfix/security release
  with binary installers for the legacy 3.7 series.

## Python v3.7.9

<https://www.python.org/ftp/python/3.7.9/python-3.7.9-amd64.exe>
