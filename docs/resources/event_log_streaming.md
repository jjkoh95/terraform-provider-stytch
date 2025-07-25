---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "stytch_event_log_streaming Resource - stytch"
subcategory: ""
description: |-
  Resource for managing event log streaming.
---

# stytch_event_log_streaming (Resource)

Resource for managing event log streaming.

## Example Usage

```terraform
# Create a Datadog destination for event log streaming.
resource "stytch_event_log_streaming" "datadog" {
  project_id       = stytch_project.consumer_project.test_project_id
  destination_type = "DATADOG"
  datadog_config {
    api_key = "0123456789abcdef0123456789abcdef"
    site    = "US"
  }
}

# Create a Grafana Loki destination for event log streaming.
resource "stytch_event_log_streaming" "grafana_loki" {
  project_id       = stytch_project.consumer_project.test_project_id
  destination_type = "GRAFANA_LOKI"
  grafana_loki_config {
    username = "stytch-logs"
    password = "password"
    hostname = "prod-01.grafana.net"
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `destination_type` (String) The type of destination to send events to.
- `project_id` (String) The unique identifier for the project.

### Optional

- `datadog_config` (Attributes) The configuration for the Datadog destination to send events to. (see [below for nested schema](#nestedatt--datadog_config))
- `grafana_loki_config` (Attributes) The configuration for the Grafana Loki destination to send events to. (see [below for nested schema](#nestedatt--grafana_loki_config))

### Read-Only

- `id` (String) A computed ID field used for Terraform resource management.
- `last_updated` (String) Timestamp of the last Terraform update of the resource.
- `streaming_status` (String) The status of streaming for this project and destination.

<a id="nestedatt--datadog_config"></a>
### Nested Schema for `datadog_config`

Required:

- `api_key` (String, Sensitive) The API key for the Datadog account.
- `site` (String) The site of the Datadog account.


<a id="nestedatt--grafana_loki_config"></a>
### Nested Schema for `grafana_loki_config`

Required:

- `hostname` (String) The hostname of the Grafana Loki instance. Custom protocols and paths are not supported.
- `password` (String, Sensitive) The password for the Grafana Loki instance.
- `username` (String) The username for the Grafana Loki instance.

## Import

Import is supported using the following syntax:

```shell
# A Stytch event log streaming destination can be imported by specifying the relevant project ID and the destination ID
# Note that the sensitive values are not imported, and will need to be set manually.
terraform import stytch_event_log_streaming.datadog project-live-00000000-0000-0000-0000-000000000000.DATADOG
```
