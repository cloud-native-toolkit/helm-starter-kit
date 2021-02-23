# Starter Kit helm starter

Helm starter used to enable starter kits via `helm create --starter ...`. This can be used in conjunction with the [Starter helm plugin](https://github.com/ibm-garage-cloud/helm-plugin-starter) to easily install the starter locally.

## Installation

### Installing with the `Starter` helm plugin

1. Install the `Starter` helm plugin

    ```shell
    helm plugin install https://github.com/ibm-garage-cloud/helm-plugin-starter.git
    ```

2. Fetch the starter

    ```shell
    helm starter fetch https://github.com/ibm-garage-cloud/helm-starter-kit --name starter-kit
    ```

### Installing manually

1. Create the starters directory (if it doesn't already exist)

    ```shell
    mkdir -p ${HOME}/.helm/starters
    ```

2. Clone the starter repo into the starters directory

    ```shell
    git clone https://github.com/ibm-garage-cloud/helm-starter-kit ${HOME}/.helm/starters/starter-kit
    ```

## Updates

The starters can be updated in-place by pulling the latest from the Git repo.

### Updating with the `Starter` helm plugin

```shell
helm starter update starter-kit
```

### Updating manually
```shell
cd ${HOME}/.helm/starters/starter-kit
git pull
```

## Usage

Helm allows the usage of a "template" chart when creating other charts, as follows:

```shell
helm create ${CHART_NAME} --starter=starter-kit 
```

This will create an initial chart based off of the `helm-starter-kit` boilerplate that can be repeated for
multiple projects. Helm uses named values with the format of `__PLACEHOLDER__` to customize certain values from the starter when the new chart is created. Anything that needs further attention
once the chart has been generated should have a `todo` and extensive documentation.

A list of the `__` placeholders and their intended purpose is below:

* `__NAME__`: The human readable name of the chart of the form `/A-Za-z-_ /` e.g. `inventory-svc`
* `__CHART__`: The reference of the chart of the form `/a-z/` e.g. `base`.
* `__CONTAINER_NAME__`:  The name of the application container of the form `a-z` e.g. `base`
* `__CONTAINER_IMAGE__`: The image ref of the container to be used of the form `/a-z.\//-_` e.g. `bitnami/nginx`

## Development

There are various parts of the charts that cannot be automatically generated, and will require a user to make these
decisions. However, since Helm is a newer technology and not all users are as well versed with either it, or Kubernetes,
the sections have been heavily documented. The documentation follows the same syntax as the values.yaml syntax that
seems common in upstream helm. A commented out code line that is supposed to be included looks as follows, with a single
`#` character

```yaml
# thisIsACommentedOutCodeLine: "value"
```

A comment that explains the purpose of this code, or other helpful information has two `##` characters

```yaml
## This is explanatory text, that indicates what is going on with a given line of code.
```
