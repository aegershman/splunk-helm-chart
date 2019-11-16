# splunk-helm-chart

releasing

```sh
# Create a *.tgz of the helm chart, place it in the /docs folder
helm package splunk --destination docs

# Rebuild the `index.yml` to include the newly-created *.tgz
helm repo index docs --url https://aegershman.github.io/splunk-helm-chart/

# git add, git commit, git push, etc.
```

## `splunk-apps/`

Currently this forces on `rfc5424-syslog` app in `splunk-apps/` folder. I'd like to figure out a better, more dyanmic way of including user-provided app `tgz`s.

[+1 thanks to `rfc5424-syslog` built by David Millis](https://splunkbase.splunk.com/app/978/) and their use of [ccBY3.0 license](https://creativecommons.org/licenses/by/3.0/)

Until then, if you'd like to use both the included `rfc5424-syslog` app and apps directly from `splunkbase`, your `values.yml` will end up overriding the default `apps_locations`, so you'll need to include `"/tmp/apps/rfc5424-syslog_11.tgz"`. Your values will look something like this:

```yml
splunk:
  defaultYml:
    splunk:
      apps_locations:
        - "/tmp/apps/rfc5424-syslog_11.tgz"
        - https://splunkbase.splunk.com/app/978/release/1.1/download
```

## `curl` for testing locally

```sh
#!/usr/bin/env bash

case "$1" in
http)
  curl -k "http://splunk.127.0.0.1.xip.io:8080/services/collector/event" \
    -H "Authorization: Splunk b51a8063-8316-4433-8963-a9af78afce17" \
    -d '{"event": "Hello, world!", "sourcetype": "manual"}'
  ;;

https)
  curl -k "https://splunk.127.0.0.1.xip.io:4443/services/collector/event" \
    -H "Authorization: Splunk b51a8063-8316-4433-8963-a9af78afce17" \
    -d '{"event": "Hello, world!", "sourcetype": "manual"}'
  ;;
esac
```
