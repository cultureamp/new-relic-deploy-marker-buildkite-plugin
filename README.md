New Relic Deployment Marker Buildkite Plugin
===============================

A [Buildkite plugin](https://buildkite.com/docs/agent/plugins) to create a [New Relic deployment marker](https://docs.newrelic.com/docs/apm/new-relic-apm/maintenance/record-deployments#post-deployment).


Example
-------

```yml
  - name: "Deploy Production"
    command: 'bin/ci_deploy'
    plugins:
      - cultureamp/new-relic-deploy-marker:
          app_id: 123456789
```

The New Relic API key can be read from an environment variable `NEW_RELIC_API_KEY` or by setting the plugin property `api_key`. The key can also be retrieved from SSM Parameter Store by setting the plugin property `api_key_ssm_param_name`. **Note: If using Parameter store ensure that the key exists and your build agent has access to it.**

Options
-------

### `app_id`

The New Relic application ID. To locate the app ID from the New Relic UI:

1. Go to rpm.newrelic.com/apm  > (select an app).
2. In the URL bar, copy the number after the /applications/ section of the URL

### `api_key` (optional)

The New Relic REST API key.

### `api_key_ssm_param_name` (optional)

New Relic REST API key parameter name in AWS SSM. Defaults to `/NEW_RELIC_API_KEY`.

### `description` (optional)

A high-level description of this deployment, visible in the Overview page and on the Deployments page when you select an individual deployment. Defaults to `BUILDKITE_BUILD_URL`.

### `user` (optional)

A username to associate with the deployment, visible in the Overview page and on the Deployments page. Defaults to `BUILDKITE_BUILD_CREATOR_EMAIL`.


References
----------

* [Record a deployment with POST](https://docs.newrelic.com/docs/apm/new-relic-apm/maintenance/record-deployments#post-deployment)
* [Find the New Relic product ID](https://docs.newrelic.com/docs/apis/rest-api-v2/requirements/find-product-id#apm)
