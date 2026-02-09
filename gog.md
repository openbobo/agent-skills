# Google Workspace CLI (gog)

## Setup
```bash
# Install
brew install steipete/tap/gogcli

# Auth setup
gog auth credentials /path/to/client_secret.json
gog auth add you@gmail.com --services gmail,calendar,drive,contacts,sheets,docs

# List accounts
gog auth list
```

## Gmail
```bash
# Search emails
gog gmail search 'newer_than:7d' --max 10

# Send email
gog gmail send --to a@b.com --subject "Hi" --body "Hello"
```

## Calendar
```bash
# List events
gog calendar events <calendarId> --from 2026-02-01 --to 2026-02-28
```

## Drive
```bash
# Search files
gog drive search "query" --max 10
```

## Contacts
```bash
# List contacts
gog contacts list --max 20
```

## Sheets
```bash
# Get values
gog sheets get <sheetId> "Tab!A1:D10" --json

# Update values
gog sheets update <sheetId> "Tab!A1:B2" --values-json '[["A","B"],["1","2"]]'

# Append rows
gog sheets append <sheetId> "Tab!A:C" --values-json '[["x","y","z"]]'
```

## Docs
```bash
# Export
gog docs export <docId> --format txt --out /tmp/doc.txt

# Read content
gog docs cat <docId>
```

## Environment
```bash
# Set default account
export GOG_ACCOUNT=you@gmail.com
```

---

*From gog skill (SKILL.md)*
