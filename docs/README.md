# Sophos Central Integration

The [Sophos Central](https://www.sophos.com/en-us/products/sophos-central) integration allows you to monitor Alerts and Events logs. Sophos Central is a cloud-native application with high availability. It is a cybersecurity management platform hosted on public cloud platforms. Each Sophos Central account is hosted in a named region. Sophos Central uses well-known, widely used, and industry-standard software libraries to mitigate common vulnerabilities.

Use the Sophos Central integration to collect logs across Sophos Central managed by your Sophos account.
Visualize that data in Kibana, create alerts to notify you if something goes wrong, and reference data when troubleshooting an issue.

## Data streams

The Sophos Central integration collects logs for two types of events: alerts and events.


**Events**: See Example Schema [here](https://developer.sophos.com/docs/siem-v1/1/routes/events/get) for more information.

## Compatibility

The Sophos Central Application does not feature version numbers. This integration has been configured and tested against **Sophos Central SIEM Integration API version v1**.

## Requirements

You need Elasticsearch for storing and searching your data, and Kibana for visualizing and managing it. You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your own hardware.

## Setup

### Elastic Integration for Sophos Central Settings

Follow this [link](https://developer.sophos.com/getting-started-tenant) to guide you through the process of generating authentication credentials for Sophos Central.

The Elastic Integration for Sophos Central requires the following Authentication Settings in order to connect to the Target service:
  - Client ID
  - Client Secret
  - Grant Type
  - Scope
  - Tenant ID
  - Token URL (without the URL path)

**NOTE**: Sophos central supports logs only upto last 24 hrs.

## Logs reference

### Events

This is the `events` dataset.

#### Example

An example event for `event` looks as following:

```json
{
    "@timestamp": "2022-12-06T12:27:28.094Z",
    "agent": {
        "ephemeral_id": "5347e925-6d9e-4a32-bda5-1785fd44709f",
        "id": "cf659b85-d5b7-4b0d-8b9a-4ea2e187d862",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "8.7.1"
    },
    "data_stream": {
        "dataset": "sophos_central.event",
        "namespace": "ep",
        "type": "logs"
    },
    "destination": {
        "ip": "81.2.69.192",
        "port": 789
    },
    "ecs": {
        "version": "8.11.0"
    },
    "elastic_agent": {
        "id": "cf659b85-d5b7-4b0d-8b9a-4ea2e187d862",
        "snapshot": false,
        "version": "8.7.1"
    },
    "event": {
        "action": "Malicious inbound network traffic blocked from remote computer at 192.168.0.2 (Technical Support reference: 2019052901.77863414.5)",
        "category": [
            "host"
        ],
        "created": "2022-12-06T12:27:31.310Z",
        "dataset": "sophos_central.event",
        "id": "3dab71db-32c9-426a-8616-1e0fd5c9aab9",
        "ingested": "2023-05-24T14:38:29Z",
        "kind": [
            "event"
        ],
        "original": "{\"created_at\":\"2022-12-06T12:27:31.310Z\",\"customer_id\":\"d1271b33-4e24-4cc3-951a-badc38976ca3\",\"endpoint_id\":\"fb11564b-2882-44ea-ac64-d1bfb041ab49\",\"endpoint_type\":\"computer\",\"group\":\"RUNTIME_DETECTIONS\",\"id\":\"3dab71db-32c9-426a-8616-1e0fd5c9aab9\",\"ips_threat_data\":{\"detectionType\":0,\"executableName\":\"\",\"localPort\":\"123\",\"rawData\":\"Message       OS-WINDOWS Microsoft Windows SMB remote code execution attempt\\nReference     CVE-2017-0146\\nPacket type   TCP\\nLocal IP:     81.2.69.192\\nLocal Port:   123\\nLocal MAC:    00:50:56:81:62:41\\nRemote IP:    81.2.69.192\\nRemote Port:  789\\nRemote MAC:   00:1C:B3:09:85:15\",\"remoteIp\":\"81.2.69.192\",\"remotePort\":\"789\",\"techSupportId\":\"2019052901.77863414.5\"},\"location\":\"Lightning-4naq56bx4j\",\"name\":\"Malicious inbound network traffic blocked from remote computer at 192.168.0.2 (Technical Support reference: 2019052901.77863414.5)\",\"severity\":\"low\",\"source\":\"Lightning-a3i691l7cv\\\\Lightning\",\"source_info\":{\"ip\":\"81.2.69.192\"},\"threat\":\"IPS/Inbound/7777001\",\"type\":\"Event::Endpoint::Threat::IpsInboundDetection\",\"user_id\":\"638f34e1e5d0a20f3d40cf93\",\"when\":\"2022-12-06T12:27:28.094Z\"}",
        "type": [
            "info"
        ]
    },
    "input": {
        "type": "httpjson"
    },
    "organization": {
        "id": "d1271b33-4e24-4cc3-951a-badc38976ca3"
    },
    "related": {
        "ip": [
            "81.2.69.192"
        ]
    },
    "sophos_central": {
        "event": {
            "created_at": "2022-12-06T12:27:31.310Z",
            "customer_id": "d1271b33-4e24-4cc3-951a-badc38976ca3",
            "endpoint": {
                "id": "fb11564b-2882-44ea-ac64-d1bfb041ab49",
                "type": "computer"
            },
            "group": "RUNTIME_DETECTIONS",
            "id": "3dab71db-32c9-426a-8616-1e0fd5c9aab9",
            "ips_threat_data": {
                "detection_type": 0,
                "local_port": 123,
                "raw_data": {
                    "local": {
                        "ip": "81.2.69.192",
                        "mac": "00-50-56-81-62-41",
                        "port": 123
                    },
                    "message": "OS-WINDOWS Microsoft Windows SMB remote code execution attempt",
                    "original": "Message       OS-WINDOWS Microsoft Windows SMB remote code execution attempt\nReference     CVE-2017-0146\nPacket type   TCP\nLocal IP:     81.2.69.192\nLocal Port:   123\nLocal MAC:    00:50:56:81:62:41\nRemote IP:    81.2.69.192\nRemote Port:  789\nRemote MAC:   00:1C:B3:09:85:15",
                    "packet_type": "TCP",
                    "reference": "CVE-2017-0146",
                    "remote": {
                        "ip": "81.2.69.192",
                        "mac": "00-1C-B3-09-85-15",
                        "port": 789
                    }
                },
                "remote": {
                    "ip": "81.2.69.192",
                    "port": 789
                },
                "tech_support_id": "2019052901.77863414.5"
            },
            "location": "Lightning-4naq56bx4j",
            "name": "Malicious inbound network traffic blocked from remote computer at 192.168.0.2 (Technical Support reference: 2019052901.77863414.5)",
            "severity": "low",
            "source": {
                "domain": {
                    "name": "Lightning-a3i691l7cv"
                },
                "original": "Lightning-a3i691l7cv\\Lightning",
                "user": {
                    "name": "Lightning"
                }
            },
            "source_info": {
                "ip": "81.2.69.192"
            },
            "threat": "IPS/Inbound/7777001",
            "type": "Event::Endpoint::Threat::IpsInboundDetection",
            "user_id": "638f34e1e5d0a20f3d40cf93",
            "when": "2022-12-06T12:27:28.094Z"
        }
    },
    "source": {
        "ip": "81.2.69.192",
        "port": 123
    },
    "tags": [
        "preserve_original_event",
        "preserve_duplicate_custom_fields",
        "forwarded",
        "sophos_central-event"
    ],
    "threat": {
        "feed": {
            "name": "IPS/Inbound/7777001"
        }
    },
    "user": {
        "domain": "Lightning-a3i691l7cv",
        "id": "638f34e1e5d0a20f3d40cf93",
        "name": "Lightning"
    }
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| event.dataset | Event dataset. | constant_keyword |
| event.module | Event module. | constant_keyword |
| input.type | Type of Filebeat input. | keyword |
| log.offset | Log offset. | long |
| log.source.address | Source address from which the log event was read / sent from. | keyword |
| sophos_central.event.amsi_threat_data.parent_process.id | Parent process id of amsi_threat_data. | keyword |
| sophos_central.event.amsi_threat_data.parent_process.path | Parent process path of amsi_threat_data. | keyword |
| sophos_central.event.amsi_threat_data.process.id | Process ID of amsi_threat_data. | keyword |
| sophos_central.event.amsi_threat_data.process.name | Process name of amsi_threat_data. | keyword |
| sophos_central.event.amsi_threat_data.process.path | Process path of amsi_threat_data. | keyword |
| sophos_central.event.app_certs.signer | Certificate info of the singer with the threat, if available. | keyword |
| sophos_central.event.app_certs.thumbprint | Certificate info of the thumbprint with the threat, if available. | keyword |
| sophos_central.event.app_sha256 | SHA 256 hash of the application associated with the threat, if available. | keyword |
| sophos_central.event.core_remedy.items.descriptor | Descriptor of Core remedy items. | keyword |
| sophos_central.event.core_remedy.items.process_path | Process path of core remedy items. | keyword |
| sophos_central.event.core_remedy.items.result | The following values are allowed NOT_APPLICABLE, SUCCESS, NOT_FOUND, DELETED, FAILED_TO_DELETE, WHITELISTED, OTHER_ERROR, FAILED_TO_DELETE_SYSTEM_PROTECTED. | keyword |
| sophos_central.event.core_remedy.items.sophos_pid | Sophos process ID. | keyword |
| sophos_central.event.core_remedy.items.suspend_result | Suspend result of core remedy items. | keyword |
| sophos_central.event.core_remedy.items.type | Type of Core remedy items. | keyword |
| sophos_central.event.core_remedy.total_items | Total items of core remedy. | long |
| sophos_central.event.created_at | The date at which the event was created. | date |
| sophos_central.event.customer_id | The identifier of the customer for which record is created. | keyword |
| sophos_central.event.endpoint.id | The corresponding endpoint id associated with the record. | keyword |
| sophos_central.event.endpoint.type | The corresponding endpoint type associated with the record. | keyword |
| sophos_central.event.group | The group associated with the group. | keyword |
| sophos_central.event.id | The Identifier for the event. | keyword |
| sophos_central.event.ips_threat_data.detection_type | Detection type of IPS threat. | long |
| sophos_central.event.ips_threat_data.executable.name | Name of executable ips threat. | keyword |
| sophos_central.event.ips_threat_data.executable.path | Path of executable ips threat. | keyword |
| sophos_central.event.ips_threat_data.executable.pid | Process id of executable ips threat. | long |
| sophos_central.event.ips_threat_data.executable.version | Version of executable ips threat. | keyword |
| sophos_central.event.ips_threat_data.local_port | Local port of IPS threat. | long |
| sophos_central.event.ips_threat_data.raw_data.executable | Executable raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.local.ip | Local ip in raw data of IPS threat. | ip |
| sophos_central.event.ips_threat_data.raw_data.local.mac | Local mac in raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.local.port | Local port in raw data of IPS threat. | long |
| sophos_central.event.ips_threat_data.raw_data.message | Original raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.original | Original raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.packet_type | Packet type in raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.pid | PID raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.reference | Original raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.remote.ip | Remote IP in raw data of IPS threat. | ip |
| sophos_central.event.ips_threat_data.raw_data.remote.mac | Remote mac in raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.remote.port | Remote port in raw data of IPS threat. | long |
| sophos_central.event.ips_threat_data.raw_data.sha_256 | SHA 256 code of raw data. | keyword |
| sophos_central.event.ips_threat_data.raw_data.signer | Signer raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.raw_data.version | Version raw data of IPS threat. | keyword |
| sophos_central.event.ips_threat_data.remote.ip | Remote IP of IPS threat. | ip |
| sophos_central.event.ips_threat_data.remote.port | Remote Port of IPS threat. | long |
| sophos_central.event.ips_threat_data.tech_support_id | Tech support ID of IPS threat. | keyword |
| sophos_central.event.location | The location captured for this record. | keyword |
| sophos_central.event.name | The name of the record created. | keyword |
| sophos_central.event.origin | Originating component of a detection. | keyword |
| sophos_central.event.severity | The severity of the threat reported by the event; possible values are None (0), Low (1), Medium (2), High (3), Critical (4). | keyword |
| sophos_central.event.source.domain.name | Domain name of source. | keyword |
| sophos_central.event.source.original | Describes the source from alert was generated. | keyword |
| sophos_central.event.source.user.name | Username of source. | keyword |
| sophos_central.event.source_info.ip | Detailed source information for IP. | ip |
| sophos_central.event.threat | The threat associated with the record. | keyword |
| sophos_central.event.type | The type of this record. | keyword |
| sophos_central.event.user_id | The identifier of the user for which record is created. | keyword |
| sophos_central.event.when | The date at which the event was created. | date |
