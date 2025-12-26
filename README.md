# Bambu Lab Error Logger

A Home Assistant blueprint that logs Bambu Lab printer errors to the logbook for historical tracking.

## Why?

The [ha-bambulab](https://github.com/greghesp/ha-bambulab) integration exposes print errors and HMS errors as binary sensors, but the error details (code, message, severity, wiki link) are stored as attributes. Home Assistant doesn't record attribute history by default, so this blueprint captures those details in the logbook when errors occur.

## Requirements

- [ha-bambulab](https://github.com/greghesp/ha-bambulab) integration installed and configured

## One-Click Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Flogikal%2Fbambu_hass_blueprints%2Fblob%2Fmain%2Fautomation%2Fbambu_error_logger.yaml)

## Manual Installation

1. Download `bambu_error_logger_blueprint.yaml`
2. Copy to `/config/blueprints/automation/bambu_error_logger.yaml`
3. Restart Home Assistant or reload automations
4. Go to **Settings → Automations → Create Automation → Use Blueprint**
5. Select your print error and HMS error sensors (supports multiple printers)

## Viewing Logs

Logged errors appear in:

- **Activity panel**: Sidebar → History → Logbook tab (filter by your error entities)
- **Entity detail**: Click any error sensor → scroll to activity section
- **Dashboard card**:

```yaml
type: logbook
title: Bambu Printer Errors
entities:
  - binary_sensor.YOUR_PRINTER_print_error
  - binary_sensor.YOUR_PRINTER_hms_errors
hours_to_show: 168
```

## Log Format Examples

**Print errors:**

```text
H2D: Print Error [0500_8061]: No print plate detected. Please make sure it is placed correctly.
```

**HMS errors:**

```text
X1C: HMS SERIOUS [HMS_0300_1200_0002_0001]: The front cover of the toolhead fell off. (https://wiki.bambulab.com/...)
```

## License

MIT