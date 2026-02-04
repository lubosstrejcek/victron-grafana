# Victron Grafana

Grafana dashboards for visualizing Victron Energy monitoring data.

**Created by Lubos Strejcek during [Victron Energy Training Center Brno](https://www.victronenergy.com/) - Node-RED Training**

> This repository is public and free to use for inspiration or as a starting point for your own Victron monitoring setup.

## Overview

Pre-configured Grafana with **zero manual setup**:
- 5 dashboards auto-loaded on startup
- InfluxDB data source auto-configured
- Just run `docker compose up -d` and open browser

## Quick Start

```bash
# Clone and run
git clone https://github.com/lubosstrejcek/victron-grafana.git
cd victron-grafana
cp .env.example .env
docker compose up -d

# Access UI
open http://localhost:3000
# Login: admin / victron123
```

**Note:** Requires InfluxDB running. See [victron-influxdb](https://github.com/lubosstrejcek/victron-influxdb).

## Dashboards

| Dashboard | Description |
|-----------|-------------|
| **Overview** | Live metrics, today's energy (Home) |
| **Energy** | Power flow, EV charging, battery history |
| **Environment** | Sensors, tanks, Shelly control |
| **System** | GX/MQTT status, Docker stats |
| **Errors** | Detailed error analysis |

## Auto-Provisioning

Everything is automatically configured on container start:

```
provisioning/
├── datasources/
│   └── influxdb.yml      # InfluxDB connection (auto-configured)
└── dashboards/
    ├── victron.yml       # Dashboard provider config
    └── json/
        ├── victron-overview.json
        ├── victron-energy.json
        ├── victron-env.json
        ├── victron-sys.json
        └── errors.json
```

No manual import or configuration needed. Dashboards appear in the "Victron Energy" folder.

## Related Repositories

- [victron-nodered](https://github.com/lubosstrejcek/victron-nodered) - Node-RED flows
- [victron-influxdb](https://github.com/lubosstrejcek/victron-influxdb) - InfluxDB configuration

## License

MIT License

## Acknowledgments

- [Victron Energy Training Center Brno](https://www.victronenergy.com/)
