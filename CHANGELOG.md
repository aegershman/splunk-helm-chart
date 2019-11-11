# changelog

This is a crummy changelog. Sue me.

## [0.17.3]

* support local apps from a `tgz` in configMap format

## [0.17.2]

* support pulling apps from splunkbase
* update ci example to pull syslog app from splunkbase
* has not been tested for storing apps locally in tgz format

## [0.17.1]

* add `debug` option tying into splunk-ansible vars
* specify `debug` in ci test

## [0.17.0]

* add `mgmt` (`svc`) port, `8089` by default
* this is referred to as `svcPort` so I guess I should use that naming
* in ci test rename `splunk` deployment to `splunk-forwarders`
* add ci test `nginx-ingress` tcp proxy for `8089`
* add taskfile `splunk-logs` & `nginx-logs`

## [0.16.1]

* cuts an actual release
* makes sure the appVersion is 8.0.0 instead of 7.0.3, that should've been fixed in previous release my bad

## [0.16.0]

* move from `7.0.3` of docker-legacy to `8.0.0` image
* basic-ish use of `defaults.yml` as per [the splunk-ansible and operator repo](https://github.com/splunk/splunk-ansible/blob/develop/docs/advanced/default.yml.spec.md#example)
* remove httpconfig configmap
* removes globalToken in favor of hec_token in defaults.yml
* removes enableSSL on hec in favor of hec_enableSSL from defaults
* removes adminPassword in favor of defaults
* removes configmaps for transforms and props and such in favor of yaml properties
* rm comment on configmap changes rolling deployments
* REMOVES and DOES NOT SOLVE the rfc5245 app issue yet, will do that in separate release

## [0.15.0]

* temporarily remove probes because I'm a dingus and can't get them to play nice locally

## [0.14.0]

* reorders app-related config params under `splunk` key

## [0.13.0]

* revision limits to prevent tons of replicasets

## [0.12.3]

* comments at top of values yml

## [0.12.2]

* adds deployment strategy options

## [0.12.1]

* fix label selector for affinity

## [0.12.0]

* adds probes. probe me, ~~aliens~~ ~~tsa~~ daddy.
* finally, this allows an actual rolling update
* should be able to roll the deployment w/o losing logs now

## [0.11.3]

* moves 'splunk' chart up a layer out of "charts"
* just cosmetic

## [0.11.2]

* Roll deployment on configmap changes
* turn off recreate pods on local dev
* still requires an update strategy, testing, investigation, etc.

## [0.11.1]

* Forgot to update the connection test earlier

## [0.11.0]

* prefixes configmap names with the chart name
* allows for better config namespacing

## [0.10.1]

* configurable global HEC TLS option (on by default)

## [0.10.0]

* ingress handles both `web` and `hec`
* still lots of work to do on this
* local example ingress now forwards http (8080) and https (4443)

## [0.9.0]

* move `web.service.annotations` under `service.annoations`

## [0.8.0]

* ingress and svc improvements
* use named ports
* ports are configurable now
* rename pas-syslog to syslog
* local testing exposes endpoints
* local testing deactivates default backend
* local testing deactivates http and https to save nodeports 80 and 443
* local testing forwards 8000 and 8088

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
