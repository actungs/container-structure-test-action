# Container Structure Test Action

An action to setup, cache and run the [GoogleContainerTools/container-structure-test](https://github.com/GoogleContainerTools/container-structure-test) executable.

[actions/cache](https://github.com/actions/cache) is used to cache the executable under `<OS name>-container-structure-test`.

The cache should be deleted if the executable should be re-installed.

> [!NOTE]
> Currently this action only supports Linux and macOS GitHub runners.

## Usage

```yaml
- uses: actungs/container-structure-test-action@v1
  with:
    # The full docker image tag to be verified.
    #
    # Required.
    image: ''

    # The path to the container structure configuration files.
    #
    # Required.
    config_files: ''

    # The version of container-structure-test to be installed.
    # See the key property in https://storage.googleapis.com/container-structure-test for available versions.
    #
    # Default: 'latest'
    version: ''

    # The path to where the executable will be installed to.
    #
    # Default: '.bin'
    install_path: ''

    # Set to 'false' if color should be used in the output.
    #
    # Default: 'true'
    no_color: ''

    # Set to 'true' to force a pull of the image before running the tests.
    #
    # Default: 'false'
    pull_image: ''

    # The output format for the test report. Available format: text, json, junit.
    #
    # Default: 'text'
    output_format: ''

    # Write the test report to the specified file. Supported file types are json and junit.
    # Set the `output_format` accordingly.
    # If the `output_format` does not match the given file type, then `json` will be used instead.
    #
    # Default: ''
    report_file: ''
```

## Example

A simplified example, on how this action can be utilized, could look like this.

```yaml
"on": [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # Build the container image
      # ...
      # Run the container test, assuming the image is 'actungs/test-image:local' and the configuration file is 'config.yaml'.
      - uses: actungs/container-structure-test-action@v1
        with:
          image: actungs/test-image:local
          config_files: config.yaml
```

## License

This project is released under the [MIT License](./LICENSE).

