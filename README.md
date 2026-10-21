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

- It starts in **dry-run** mode and only logs what it would do. The default `rules.yml` in the appdata folder includes rules that delete torrents: review it, then set **Dry run** to `false`.
- Nothing runs until something triggers it: a schedule in `config.yml`, qBittorrent's "Run external program" webhook, or a call to the HTTP API. See [Contexts](https://github.com/andronics/qbt-rules/wiki/Contexts) and [Scheduling](https://github.com/andronics/qbt-rules/wiki/Scheduling).
- Support and questions: [qbt-rules Discussions](https://github.com/andronics/qbt-rules/discussions).
