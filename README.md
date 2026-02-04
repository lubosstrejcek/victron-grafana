# Victron Grafana

Grafana dashboards for visualizing Victron Energy monitoring data.

**Created during [Victron Energy Training Center Brno](https://www.victronenergy.com/) - Node-RED Training**

## Overview

Pre-configured Grafana dashboards for Victron monitoring:
- 5 dashboards covering all aspects of energy monitoring
- InfluxDB data source configuration
- Shelly device control buttons

## Quick Start

```bash
# Run with Docker
docker run -d --name victron-grafana \
  -p 3000:3000 \
  -v $(pwd):/var/lib/grafana \
  -e GF_SECURITY_ADMIN_PASSWORD=victron123 \
  -e GF_PANELS_DISABLE_SANITIZE_HTML=true \
  grafana/grafana:latest

# Access UI
open http://localhost:3000
# Login: admin / victron123
```

## Dashboards

| Dashboard | Description |
|-----------|-------------|
| **Overview** | Live metrics, today's energy (Home) |
| **Energy** | Power flow, EV charging, battery history |
| **Environment** | Sensors, tanks, Shelly control |
| **System** | GX/MQTT status, Docker stats |
| **Errors** | Detailed error analysis |

## Dashboard Files

Dashboards are in the `dashboards/` directory:
- `victron-overview.json` - Main overview
- `victron-energy.json` - Energy details
- `victron-env.json` - Environment & devices
- `victron-sys.json` - System health
- `errors.json` - Error monitoring

## Import Dashboards

### Via UI
1. Go to Dashboards → Import
2. Upload JSON file from `dashboards/`
3. Select InfluxDB data source

### Via API
```bash
curl -X POST 'http://admin:victron123@localhost:3000/api/dashboards/db' \
  -H 'Content-Type: application/json' \
  -d @dashboards/victron-overview.json
```

## Data Source Configuration

Configure InfluxDB data source:
- **Type**: InfluxDB (Flux)
- **URL**: http://influxdb:8086
- **Organization**: victron
- **Token**: victron-lab-token
- **Default Bucket**: energy

## Related Repositories

- [victron-nodered](https://github.com/lubosstrejcek/victron-nodered) - Node-RED flows
- [victron-influxdb](https://github.com/lubosstrejcek/victron-influxdb) - InfluxDB configuration

## License

MIT License

## Acknowledgments

- [Victron Energy Training Center Brno](https://www.victronenergy.com/)
