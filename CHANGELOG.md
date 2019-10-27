# changelog

This is a crummy changelog. Sue me.

## [0.2.1]

* sync `.helmignore` and `_helpers` with what a new chart would use

## [0.2.0]

* `annotations` configurable for web service
* `affinity` rules configurable for web deployment; by default, will make best-attempt efforts to schedule pods on separate hosts
* use `apps/v1` deployment API rather than `apps/v1beta2`
* Appropriate app version and description on Chart.yaml

## [0.1.2]

* [Includes rfc5424 add-on](https://splunkbase.splunk.com/app/978/) to allow proper `host` parsing.

## [0.1.1]

* Intended to be used to forward app logs _and_ syslogs to multiple targets.
* Opens TCP port `:5514` to accept incoming PCF syslogs.

## [0.1.0]

* Initial release. Used exclusively for forwarding application logs.
