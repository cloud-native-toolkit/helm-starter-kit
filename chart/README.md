# __NAME__

## Installation

```
    # Todo: Document any required values, if they exist.
    $ helm upgrade --install path/to/__CHART__ __CHART__
```

## Configuration

All configuration values are documented in values.yaml. Check that for references, default values etc. To modify a
configuration value for a chart, you can either supply your own values.yaml overriding the default one in the repo:

```shell
helm upgrade --install path/to/__CHART__ __CHART__ --values path/to/custom/values/file.yaml
```

Or, you can override an individual configuration setting with `helm upgrade --set`

```shell
helm upgrade --install path/to/__CHART__ __CHART__ --set image.repository="your/image" --set image.tag="1.0.0"
```

## Usage

// Todo: Write up usage.
