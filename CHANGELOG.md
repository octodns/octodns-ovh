## 1.2.0 - 2026-04-03

Minor:
* Add SVCB and HTTPS record support - [#62](https://github.com/octodns/octodns-ovh/pull/62)

Patch:
* Use new [changelet](https://github.com/octodns/changelet) tooling - [#50](https://github.com/octodns/octodns-ovh/pull/50)

## v1.1.0 - 2025-07-01 - Normal TXT

* Normalize TXT records to prevent unnecessary updates

## v1.0.0 - 2025-05-04 - Long overdue 1.0

### Notedworthy Changes:

* `SPF` record support removed, records should be migrated to `TXT` before
  upgrading.

## v0.0.2 - 2022-11-20 - Less dots

* Remove extra . on the end of SRV record targets

## v0.0.1 - 2022-01-13 - Moving

#### Nothworthy Changes

* Initial extraction of OvhProvider from octoDNS core

#### Stuff

Nothing
