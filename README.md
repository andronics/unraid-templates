# Unraid templates

[Unraid](https://unraid.net) Docker templates for:

| App | Description |
|-----|-------------|
| [qbt-rules](https://github.com/andronics/qbt-rules) | Rules engine for qBittorrent: declarative YAML rules to tag, categorise, pause, throttle, force-seed or delete torrents |

## Installing

Once listed in Community Applications, search for the app name in the **Apps** tab.

Until then, on the **Docker** tab choose **Add Container**, and paste the template URL into **Template**:

```
https://raw.githubusercontent.com/andronics/unraid-templates/main/qbt-rules.xml
```

## qbt-rules notes

- It starts in **dry-run** mode and only logs what it would do: review your rules, then set **Dry run** to `false`.
- Two paths: **Config** (`/etc/qbt-rules`, read-only) holds the optional `config.yaml`; **State** (`/var/lib/qbt-rules`, writable) holds `rules.yml`, the job database and the rules editor's history. Nothing is created on first start: copy in a `rules.yml` or write one in the dashboard's editor.
- Nothing runs until something triggers it: a schedule, qBittorrent's "Run external program" (`docker exec qbt-rules qbt-rules execute --context torrent-imported --hash "%I"`), or a call to the HTTP API. See [Contexts](https://github.com/andronics/qbt-rules/wiki/Contexts) and [Scheduling](https://github.com/andronics/qbt-rules/wiki/Scheduling).
- **Upgrading from 0.10.x** (one `/config` path): 0.11 no longer reads `/config`. Before updating, follow [Upgrading to 0.11](https://github.com/andronics/qbt-rules/wiki/Upgrading-to-0.11): copy (don't move) the files from the old appdata folder into `etc/` and `state/` inside it, edit `config.yaml`, then remove the old `/config` path from the container.
- Support and questions: [qbt-rules Discussions](https://github.com/andronics/qbt-rules/discussions).
