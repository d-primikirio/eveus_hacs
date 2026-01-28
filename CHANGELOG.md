# Changelog

All notable changes to this project will be documented in this file.

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
