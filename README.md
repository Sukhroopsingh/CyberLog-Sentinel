# CyberLog Sentinel 🛡️

A Python-based security log analyzer that detects suspicious authentication activity from Linux/SSH-style logs.

## What it does

CyberLog Sentinel parses authentication logs and detects:

- Repeated failed login attempts
- Successful logins after multiple failures
- Brute-force patterns
- Suspicious activity from individual IP addresses
- Authentication activity outside a configurable time window

It produces a clear terminal report and can export findings to CSV.

## Project architecture

```text
Log file
   ↓
Parser
   ↓
Event normalization
   ↓
Detection engine
   ↓
Security findings
   ↓
Terminal / CSV report
```

## Skills demonstrated

- Python
- File handling and regular expressions
- Log parsing
- Security event analysis
- Detection logic
- Risk scoring
- CSV reporting
- Unit testing
- Defensive security / SOC fundamentals

## Requirements

- Python 3.10+
- No third-party packages required

## Run

```bash
python src/analyzer.py sample_logs/auth.log
```

Export findings:

```bash
python src/analyzer.py sample_logs/auth.log --csv reports.csv
```

Change the brute-force threshold:

```bash
python src/analyzer.py sample_logs/auth.log --threshold 5
```

Run tests:

```bash
python -m unittest discover tests -v
```

## Example findings

```text
[HIGH] 203.0.113.50 - 8 failed login attempts
[CRITICAL] 203.0.113.50 - Successful login after repeated failures
[MEDIUM] 198.51.100.23 - 3 failed login attempts
```

## Security note

The IP addresses in the sample data use documentation ranges such as `203.0.113.0/24` and `198.51.100.0/24`. They are fictional examples intended for safe testing.

This project is defensive and analyzes logs you provide. It does not attack or scan external systems.

## Future improvements

- GeoIP enrichment
- JSON output
- Real-time monitoring
- SIEM integration
- Email/Slack alerting
- Dashboard
- YARA/Sigma-style detection rules
