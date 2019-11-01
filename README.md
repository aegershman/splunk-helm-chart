# splunk-helm-chart

releasing

```bash
# Create a *.tgz of the helm chart, place it in the /docs folder
helm package splunk --destination docs

# Rebuild the `index.yml` to include the newly-created *.tgz
helm repo index docs --url https://aegershman.github.io/splunk-helm-chart/

# git add, git commit, git push, etc.
```
