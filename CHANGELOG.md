# changelog

This is a crummy changelog. Sue me.

## [0.8.0]

* ingress and svc improvements

## [0.7.3]

* rm generated reference chart

## [0.7.2]

* adds default `test` template

## [0.7.1]

* add labels to configmaps

## [0.7.0]

* adds resource config
* adds tolerations
* adds nodeselector

## [0.6.1]

* cosmetic, moves params and values around

## [0.6.0]

* adds security context options
* adds podSecurityContext options

## [0.5.0]

* adds serviceAccount option

## [0.4.3]

* adds nameOverride and fullnameOverride
* puts replicaCount at top of values because that's how default chart does it

## [0.4.2]

* introduce image pull secrets
* use `with` instead of `if`

## [0.4.1]

* fix chart description

## [0.4.0]

* use contemporary helm chart metadata prefixes
* backwards incompatible

## [0.3.0]

* configurable `ingress` for the `web`, definitely work in progress

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
