# Changelog

All notable changes to this project will be documented in this file.

## [1.4.0] - 2026-02-18

### Added
- Added internal battery voltage sensor (`vBat`) with 2 decimal precision
- Added translations for battery voltage sensor (English & Ukrainian)

### Changed
- **BREAKING**: Changed power measurement unit from `kW` to `W` for `powerMeas` sensor
  - Aligns with Home Assistant standards for power sensors
  - Historical data may need adjustment if used in energy dashboards
- Improved limit status determination logic for `subState` sensor
  - Now dynamically checks which limits are actually active instead of using static mapping
  - Priority order: Session limits (time → energy → money) → Schedule limits → User limit fallback
  - Provides more accurate status when multiple limits are configured
- Updated pilot signal conversion logic
  - Car now considered connected when `pilot >= 1` (previously only `pilot == 1`)
  - Properly detects both ready (pilot=1) and charging (pilot=2) states

### Removed
- Removed unused `LIMIT_STATUS_MAP` constant from codebase

## [1.3.0] - 2026-02-02

### Added
- Added power measurement sensor (`powerMeas`) displaying real-time charging power in kW
- Added car connected sensor (`pilot`) showing whether vehicle is plugged in (Yes/No)
- Added limit status sensor (`subState`) showing active charging restrictions:
  - No Limits / Limited by User / Limited by Schedule / Limited by Time / Limited by Energy / Limited by Cost
- Added `LIMIT_STATUS_MAP` constant for limit status translations
- Complete Ukrainian and English translations for all new sensors

### Changed
- All three new sensors enabled by default for better web interface parity
- Improved sensor value formatting with proper rounding (power: 3 decimals)

## [1.2.0] - 2026-02-02

### Added
- Added `entity_registry_enabled_default` parameter to hide diagnostic/advanced entities by default for new installations
- Cleaner initial experience with only essential monitoring entities visible

### Removed
- Removed deprecated schedule toggle switch that controlled non-functional `isAlarm` API
- Removed `time.py` platform with deprecated startTime/stopTime text inputs
- Cleaned up related translations for removed entities

### Changed
- Diagnostic entities now disabled by default: leakage sensor, session/system time, ground status
- Advanced controls now disabled by default: sync/charge buttons, timezone selector, AI voltage, advanced switches
- Only affects new installations - existing setups unchanged
- All entities remain available for advanced users to enable manually

## [1.1.0] - 2026-01-28

### Fixed
- Fixed current limit control not syncing from HA to web interface (number entities now send integer values)
- Fixed status sensor showing "Unknown" instead of actual state (updated STATUS_MAP to use correct state codes 0-7)
- Fixed system time displaying Unix timestamp instead of formatted time (now shows HH:MM:SS with timezone adjustment)
- Fixed session time displaying raw seconds (now formatted as HH:MM:SS)
- Fixed 14+ translation mismatches between integration and web interface

### Changed
- Updated Ukrainian translations to match web interface exactly:
  - "Почати зарядку" → "Відключити ліміти та розклади"
  - "Темп. корпусу" → "Температура боксу"
  - "Обмеження струму" → "Дозволений струм"
  - And more...
- Updated English translations to match web interface exactly
- Updated status sensor states to match web interface (Startup, System Test, Waiting, Connected, Charging, Charge Complete, Suspended, Error)

### Added
- Added proper device classes for better Home Assistant UI:
  - Status sensor: `SensorDeviceClass.ENUM` with all state options
  - Leakage sensor: `SensorDeviceClass.CURRENT` (keeping unit as mA)
- Added timezone offset handling for system time display using charger's `timeZone` parameter

## [1.0.2] - 2026-01-27

### Changed
- Converted all code comments and log messages to English for better international collaboration
- Updated documentation with English README and Ukrainian translation

### Added
- Added CHANGELOG.md for version tracking
- Added English readme translation

## [1.0.1] - 2026-01-27

### Fixed
- Fixed incorrect current sensor values
- Fixed incorrect power sensor values

## [1.0.0] - 2026-01-27

### Added
- Initial fork from original repository by @V-Plum
- Updated repository references to new fork location

[1.1.0]: https://github.com/d-primikirio/eveus_hacs/compare/v1.0.2...v1.1.0
[1.0.2]: https://github.com/d-primikirio/eveus_hacs/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/d-primikirio/eveus_hacs/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/d-primikirio/eveus_hacs/releases/tag/v1.0.0
