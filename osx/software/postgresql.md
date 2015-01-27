# PostgreSQL

## Installation

```ShellSession
$ brew install postgresql --with-python
```

## Configuration

* Run on boot:

  ```ShellSession
  $ ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
  ```

## Development tools

### PG Commander

#### Installation

Install from Mac App Store

## Troubleshooting

### Upgrade

If you get some errors while starting the PostgreSQL daemon after an upgrade, it means that the database should be reinitialized (*notice that the DB data will be wiped out*). To do so, run:

```ShellSession
$ rm -rf /usr/local/var/postgres
$ initdb /usr/local/var/postgres -E utf8
```
