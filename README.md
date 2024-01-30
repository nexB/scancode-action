# `@nexB/scancode-action`

Run [ScanCode.io](https://github.com/nexB/scancode.io) pipelines from your Workflows.

> [!IMPORTANT]
> The scancode-action is currently in the **alpha stage**, and we invite you to 
> contribute to its improvement. Please feel free to submit bug reports or share 
> your ideas by creating new entries in the "Issues" section. 
> Your collaboration helps us enhance the action and ensures a more stable and 
> effective tool for the community. 
> Thank you for your support!

- [Usage](#usage)
  - [Basic](#basic)
  - [Inputs](#inputs)
- [Examples](#examples)
  - [Scan repo codebase](#scan-repo-codebase)
  - [Use a specific pipeline](#use-a-specific-pipeline)
  - [Choose the output formats](#choose-the-output-formats)
  - [Define a custom project name](#define-a-custom-project-name)
- [Where does the scan results go?](#where-does-the-scan-results-go)

## Usage

### Basic

```yaml
steps:
- uses: actions/checkout@v4
- uses: nexB/scancode-action@alpha
  with:
    pipeline-name: "scan_codebase"
    output-formats: "json xlsx spdx cyclonedx"
```

### Inputs

```yaml
- uses: nexB/scancode-action@alpha
  with:
    # Name of the pipeline.
    # Default is 'scan_codebase'
    pipeline-name:

    # The list of output formats to generate.
    # Default is 'json xlsx spdx cyclonedx'
    output-formats:

    # Name of the project.
    # Default is ${GITHUB_REPOSITORY}
    project-name:

    # Python version that will be installed to run ScanCode.io
    # Default is '3.11'
    python-version:
```

## Examples

### Scan repo codebase

```yaml
steps:
- uses: nexB/scancode-action@alpha
```

### Use a specific pipeline

```yaml
- uses: nexB/scancode-action@alpha
  with:
    pipeline-name: "scan_codebase"
```

### Choose the output formats

```yaml
- uses: nexB/scancode-action@alpha
  with:
    output-formats: "json xlsx spdx cyclonedx"
```

### Define a custom project name

```yaml
- uses: nexB/scancode-action@alpha
  with:
    project-name: "my-project-name"
```

## Where are the Scan Results?

Upon completion of the workflow, you can **find the scan results** in the dedicated 
**artifacts section** at the bottom of the workflow summary page. 
Look for a file named `scanpipe-outputs` in that section. 
This file contains the outputs generated by the `scancode-action`.
