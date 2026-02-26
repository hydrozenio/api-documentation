
# Hydrozen.io API Documentation

This is the documentation for the available API endpoints, which are built around the REST architecture. All the API endpoints will return a JSON response with the standard HTTP response codes and need a Bearer Authentication via an API Key.

## Table of Contents

- [Base URL](#base-url)
- [Authentication](#authentication)
- [Uptime monitors](#uptime-monitors)
  - [Retrieve all uptime monitors](#retrieve-all-uptime-monitors)
  - [Retrieve one uptime monitor](#retrieve-one-uptime-monitor)
  - [Create uptime monitor](#create-uptime-monitor)
  - [Update uptime monitor](#update-uptime-monitor)
  - [Delete uptime monitor](#delete-uptime-monitor)
- [Heartbeat Monitors](#heartbeat-monitors)
  - [Retrieve all heartbeat monitors](#retrieve-all-heartbeat-monitors)
  - [Retrieve one heartbeat monitor](#retrieve-one-heartbeat-monitor)
  - [Create Heartbeat monitor](#create-heartbeat-monitor)
  - [Update Heartbeat monitor](#update-heartbeat-monitor)
  - [Delete Heartbeat monitor](#delete-heartbeat-monitor)
- [Domain name monitors](#domain-name-monitors)
  - [Retrieve all domain name monitors](#retrieve-all-domain-name-monitors)
  - [Retrieve one domain name monitor](#retrieve-one-domain-name-monitor)
  - [Create domain name monitor](#create-domain-name-monitor)
  - [Update domain name monitor](#update-domain-name-monitor)
  - [Delete domain name monitor](#delete-domain-name-monitor)
- [Notification handlers](#notification-handlers)
  - [Retrieve all notification handlers](#retrieve-all-notification-handlers)
  - [Retrieve one notification handler](#retrieve-one-notification-handler)
  - [Create notification handler](#create-notification-handler)
  - [Update notification handler](#update-notification-handler)
  - [Delete notification handler](#delete-notification-handler)
- [User](#user)
  - [Retrieve one user](#retrieve-one-user)
- [Server Monitors](#server-monitors)
  - [Retrieve all server monitors](#retrieve-all-server-monitors)
  - [Retrieve one server monitor](#retrieve-one-server-monitor)
  - [Delete server monitor](#delete-server-monitor)
- [Projects](#projects)
  - [Retrieve all projects](#retrieve-all-projects)
  - [Retrieve one project](#retrieve-one-project)
  - [Create Project](#create-project)
  - [Update Project](#update-project)
  - [Delete Project](#delete-project)
- [Status Pages](#status-pages)
  - [Retrieve all status pages](#retrieve-all-status-pages)
  - [Retrieve one status page](#retrieve-one-status-page)
- [Custom Domains](#custom-domains)
  - [Retrieve all custom domains](#retrieve-all-custom-domains)
  - [Retrieve one custom domain](#retrieve-one-custom-domain)
  - [Create custom domain](#create-custom-domain)
  - [Update custom domain](#update-custom-domain)
  - [Delete custom domain](#delete-custom-domain)
- [DNS monitors](#dns-monitors)
  - [Retrieve all DNS monitors](#retrieve-all-dns-monitors)
  - [Retrieve one DNS monitor](#retrieve-one-dns-monitor)
  - [Delete DNS monitor](#delete-dns-monitor)
- [Teams member](#teams-member)
  - [Retrieve all teams members](#retrieve-all-teams-members)
  - [Retrieve one teams member](#retrieve-one-teams-member)
  - [Update teams member](#update-teams-member)
  - [Delete teams member](#delete-teams-member)
- [Payments](#payments)
  - [Retrieve all payments](#retrieve-all-payments)
  - [Retrieve one payment](#retrieve-one-payment)
- [Logs](#logs)
  - [Retrieve all logs](#retrieve-all-logs)
- [Status Page Statistics](#status-page-statistics)
  - [Retrieve one status page statistics](#retrieve-one-status-page-statistics)
- [Teams](#teams)
  - [Retrieve all teams](#retrieve-all-teams)
  - [Retrieve one team](#retrieve-one-team)
  - [Create team](#create-team)
  - [Update team](#update-team)
  - [Delete team](#delete-team)
- [Team Members](#team-members)
  - [Retrieve team members](#retrieve-team-members)
  - [Create team member](#create-team-member)
  - [Update team member](#update-team-member)
  - [Delete team member](#delete-team-member)

## Base URL
```
https://app.hydrozen.io/api
```
## Authentication
All the API endpoints require an API key sent by the Bearer Authentication method.

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/{endpoint}' \
--header 'Authorization: Bearer {api_key}' \
```

## Uptime monitors
### Retrieve all uptime monitors
**Endpoint**
*GET*  `https://app.hydrozen.io/api/monitors/`
**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/monitors/' \
--header 'Authorization: Bearer {api_key}' \
```
| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |
	 	
**Response example**
```json
{
  "data": [
    {
      "id": 1,
      "project_id": 0,
      "name": "Example",
      "type": "website",
      "target": "https://example.com/",
      "port": 0,
      "settings": {
        "check_interval_seconds": 3600,
        "timeout_seconds": 1,
        "request_method": "GET",
        "request_body": "",
        "request_basic_auth_username": "",
        "request_basic_auth_password": "",
        "request_headers": [],
        "response_status_code": 200,
        "response_body": "",
        "response_headers": []
      },
      "ping_servers_ids": [
        1
      ],
      "is_ok": 1,
      "uptime": 95.5,
      "downtime": 4.5,
      "average_response_time": 500,
      "total_checks": 500,
      "total_ok_checks": 450,
      "total_not_ok_checks": 50,
      "last_check_datetime": "2021-03-25 08:27:07",
      "notifications": {
        "email_is_enabled": 0,
        "webhook": "",
        "slack": "",
        "twilio": ""
      },
      "is_enabled": false,
      "datetime": "2021-02-12 21:54:29"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/monitors?&page=1",
    "last": "https://app.hydrozen.io/api/monitors?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/monitors?&page=1"
  }
}
```

### Retrieve one uptime monitor
**Endpoint**
*GET*  `https://app.hydrozen.io/api/monitors/{monitor_id}`
**Example**
```bash
curl --request GET \  
--url 'https://app.hydrozen.io/api/monitors/{monitor_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```
**Response example**
```json
{
  "data": {
    "id": 1,
    "project_id": 0,
    "name": "Example",
    "type": "website",
    "target": "https://example.com/",
    "port": 0,
    "settings": {
      "check_interval_seconds": 3600,
      "timeout_seconds": 1,
      "request_method": "GET",
      "request_body": "",
      "request_basic_auth_username": "",
      "request_basic_auth_password": "",
      "request_headers": [],
      "response_status_code": 200,
      "response_body": "",
      "response_headers": []
    },
    "ping_servers_ids": [
      1
    ],
    "is_ok": 1,
    "uptime": 95.5,
    "downtime": 4.5,
    "average_response_time": 500,
    "total_checks": 500,
    "total_ok_checks": 450,
    "total_not_ok_checks": 50,
    "last_check_datetime": "2021-03-25 08:27:07",
    "notifications": {
      "email_is_enabled": 0,
      "webhook": "",
      "slack": "",
      "twilio": ""
    },
    "is_enabled": false,
    "datetime": "2021-02-12 21:54:29"
  }
}
```
### Create uptime monitor

**Endpoint**

*POST*  `https://app.hydrozen.io/api/monitors`

| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| target | `Required` `String` | - |
| port | `Optional` `String` | - |
| type | `Optional` `String` | Allowed values:  `website`,  `ping`,  `port` |
| project_id | `Optional` `String` | - |
| ping_servers_ids | `Optional` `Array` | Allowed values:  `1`,  `2` |
| check_interval_seconds | `Optional` `Integer` | Allowed values:  `60`,  `180`,  `300`,  `600`,  `1800`,  `3600`,  `21600`,  `43200`,  `86400`  (seconds) |
| timeout_seconds | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `5`,  `10`,  `25`  (seconds) |
| request_method | `Optional` `String` | Allowed values:  `HEAD`,  `GET`,  `POST`,  `PUT`,  `PATCH` |
| request_body | `Optional` `String` | - |
| request_basic_auth_username | `Optional` `String` | - |
| request_basic_auth_password | `Optional` `String` | - |
| request_header_name | `Optional` `Array` | - |
| request_header_value | `Optional` `Array` | - |
| response_status_code | `Optional` `Integer` | - |
| response_body | `Optional` `String` | - |
| response_header_name | `Optional` `String` | - |
| response_header_value | `Optional` `String` | - |
| is_ok_notifications | `Optional` `Array` | Notification handler ids |
| email_reports_is_enabled | `Optional` `Boolean` | - |
| is_enabled | `Optional` `boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/monitors' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
--form 'target=https://example.com/' \  
```

**Response example**

```json
{
"data": {
"id": 1
}
}
```
### Update uptime monitor

**Endpoint**

*POST*  `https://app.hydrozen.io/api/monitors/{monitor_id}`
| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| target | `Required` `String` | - |
| port | `Optional` `String` | - |
| type | `Optional` `String` | Allowed values:  `website`,  `ping`,  `port` |
| project_id | `Optional` `String` | - |
| ping_servers_ids | `Optional` `Array` | Allowed values:  `1`,  `2` |
| check_interval_seconds | `Optional` `Integer` | Allowed values:  `60`,  `180`,  `300`,  `600`,  `1800`,  `3600`,  `21600`,  `43200`,  `86400`  (seconds) |
| timeout_seconds | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `5`,  `10`,  `25`  (seconds) |
| request_method | `Optional` `String` | Allowed values:  `HEAD`,  `GET`,  `POST`,  `PUT`,  `PATCH` |
| request_body | `Optional` `String` | - |
| request_basic_auth_username | `Optional` `String` | - |
| request_basic_auth_password | `Optional` `String` | - |
| request_header_name | `Optional` `Array` | - |
| request_header_value | `Optional` `Array` | - |
| response_status_code | `Optional` `Integer` | - |
| response_body | `Optional` `String` | - |
| response_header_name | `Optional` `String` | - |
| response_header_value | `Optional` `String` | - |
| is_ok_notifications | `Optional` `Array` | Notification handler ids |
| email_reports_is_enabled | `Optional` `Boolean` | - |
| is_enabled | `Optional` `boolean` | - |


**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/monitors/{monitor_id}' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
```

**Response example**

```json
{
"data": {
"id": 1
}
}
```

### Delete uptime monitor

**Endpoint**

*DELETE*  `https://app.hydrozen.io/api/monitors/{monitor_id}`

**Example**
```bash
curl --request DELETE \  
--url 'https://app.hydrozen.io/api/monitors/{monitor_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```

## Heartbeat Monitors
### Retrieve all heartbeat monitors
**Endpoint**

 *GET*  `https://app.hydrozen.io/api/heartbeats/`
  
**Example**
```bash 
 curl --request GET \  
       --url 'https://app.hydrozen.io/api/heartbeats/' \  
       --header 'Authorization: Bearer  {api_key}' \ 
``` 
 
| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |

**Response example**
       
```json
{
  "data": [
    {
      "id": 1,
      "project_id": 0,
      "name": "Demo cron",
      "code": "12345678901112131415",
      "settings": {
        "run_interval": 1,
        "run_interval_type": "minutes",
        "run_interval_grace": 1,
        "run_interval_grace_type": "seconds"
      },
      "is_ok": 1,
      "uptime": 75.5,
      "downtime": 24.5,
      "total_runs": 50,
      "total_missed_runs": 15,
      "last_run_datetime": "2021-03-30 19:17:22",
      "notifications": {
        "email_is_enabled": 0,
        "webhook": "",
        "slack": "",
        "twilio": ""
      },
      "is_enabled": true,
      "datetime": "2021-03-09 11:30:20"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/heartbeats?&page=1",
    "last": "https://app.hydrozen.io/api/heartbeats?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/heartbeats?&page=1"
  }
} 
```
       
## Retrieve one heartbeat monitor
**Endpoint**
*GET*  `https://app.hydrozen.io/api/heartbeats/{heartbeat_id}`   

**Example** 
```bash 
  curl --request GET \  
       --url 'https://app.hydrozen.io/api/heartbeats/{heartbeat_id}' \  
       --header 'Authorization: Bearer  {api_key}' \ 
 ```
**Response example**      
```json
{
  "data": {
    "id": 1,
    "project_id": 0,
    "name": "Demo cron",
    "code": "12345678901112131415",
    "settings": {
      "run_interval": 1,
      "run_interval_type": "minutes",
      "run_interval_grace": 1,
      "run_interval_grace_type": "seconds"
    },
    "is_ok": 1,
    "uptime": 75.5,
    "downtime": 24.5,
    "total_runs": 50,
    "total_missed_runs": 15,
    "last_run_datetime": "2021-03-30 19:17:22",
    "notifications": {
      "email_is_enabled": 0,
      "webhook": "",
      "slack": "",
      "twilio": ""
    },
    "is_enabled": true,
    "datetime": "2021-03-09 11:30:20"
  }
}
```
### Create Heartbeat monitor

**Endpoint**

*POST*  `https://app.hydrozen.io/api/heartbeats`

| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| run_interval | `Optional` ` Integer | - |
| run_interval_type | `Optional` `String` | Allowed values:  `seconds`,  `minutes`,  `hours`,  `days` |
| run_interval_grace | `Optional` `Integer` | - |
| run_interval_grace_type | `Optional` `String` | Allowed values:  `seconds`,  `minutes`,  `hours`,  `days` |
| is_ok_notifications | `Optional` `Array` | Notification ids handler |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/heartbeats' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
--form 'target=example.com' \  
```

**Response example**
```json
{
"data": {
"id": 1
}
}
```
### Update Heartbeat monitor

**Endpoint**

*POST*  `https://app.hydrozen.io/api/heartbeats/{heartbeat_id}`

| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| run_interval | `Optional` ` Integer | - |
| run_interval_type | `Optional` `String` | Allowed values:  `seconds`,  `minutes`,  `hours`,  `days` |
| run_interval_grace | `Optional` `Integer` | - |
| run_interval_grace_type | `Optional` `String` | Allowed values:  `seconds`,  `minutes`,  `hours`,  `days` |
| is_ok_notifications | `Optional` `Array` | Notification ids handler |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/heartbeats/{heartbeat_id}' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
```

**Response example**

```json
{
  "data": {
    "id": 1
  }
}
```

### Delete Heartbeat monitor

**Endpoint**
*DELETE*  `https://app.hydrozen.io/api/heartbeats/{heartbeat_id}`

**Example**
```bash
curl --request DELETE \  
--url 'https://app.hydrozen.io/api/heartbeats/{heartbeat_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```
## Domain name monitors

### Retrieve all domain name monitors

**Endpoint**
*GET*  `https://app.hydrozen.io/api/domain-names/`

**Example**
```bash
curl --request GET \  
--url 'https://app.hydrozen.io/api/domain-names/' \  
--header 'Authorization: Bearer  {api_key}' \
```
| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer`  | The page number that you want results from. Defaults to  `1`. |
| results_per_page | `Optional` `Integer`  | How many results you want per page. Allowed values are:  `10`  ,  `25`  ,  `50`  ,  `100`  ,  `250`  ,  `500`  ,  `1000`. Defaults to  `25`. |

**Response example**
```json
{
  "data": [
    {
      "id": 1,
      "project_id": 0,
      "name": "Hydrozen.io",
      "target": "hydrozen.io",
      "whois": {
        "start_datetime": "2019-12-15 18:03:36",
        "updated_datetime": "2020-05-24 15:37:15",
        "end_datetime": "2022-12-15 18:03:36",
        "registrar": "NAMECHEAP INC",
        "nameservers": [
          "ns1.digitalocean.com",
          "ns2.digitalocean.com",
          "ns3.digitalocean.com"
        ]
      },
      "whois_notifications": null,
      "ssl": {
        "organization": "Let's Encrypt",
        "common_name": "R3",
        "start_datetime": "2021-06-05 14:40:13",
        "end_datetime": "2021-09-03 14:40:13"
      },
      "ssl_notifications": null,
      "total_checks": 25,
      "last_check_datetime": "2021-07-01 14:42:14",
      "next_check_datetime": "2021-07-04 14:42:15",
      "is_enabled": true,
      "last_datetime": null,
      "datetime": "2021-03-09 11:30:20"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/domain-names?&page=1",
    "last": "https://app.hydrozen.io/api/domain-names?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/domain-names?&page=1"
  }
}
```

### Retrieve one domain name monitor

**Endpoint**
*GET*  `https://app.hydrozen.io/api/domain-names/{domain_name_id}`

**Example**
```bash
curl --request GET \  
--url 'https://app.hydrozen.io/api/domain-names/{domain_name_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```
**Response example**

```json
{
  "data": {
    "id": 1,
    "project_id": 0,
    "name": "Hydrozen.io",
    "target": "hydrozen.io",
    "whois": {
      "start_datetime": "2019-12-15 18:03:36",
      "updated_datetime": "2020-05-24 15:37:15",
      "end_datetime": "2022-12-15 18:03:36",
      "registrar": "NAMECHEAP INC",
      "nameservers": [
        "ns1.digitalocean.com",
        "ns2.digitalocean.com",
        "ns3.digitalocean.com"
      ]
    },
    "whois_notifications": null,
    "ssl": {
      "organization": "Let's Encrypt",
      "common_name": "R3",
      "start_datetime": "2021-06-05 14:40:13",
      "end_datetime": "2021-09-03 14:40:13"
    },
    "ssl_notifications": null,
    "total_checks": 25,
    "last_check_datetime": "2021-07-01 14:42:14",
    "next_check_datetime": "2021-07-04 14:42:15",
    "is_enabled": true,
    "last_datetime": null,
    "datetime": "2021-03-09 11:30:20"
  }
}
```

### Create domain name monitor

**Endpoint**

*POST*  `https://app.hydrozen.io/api/domain-names`
| Parameters | Details | Description |  
|--|--|--|
| name | `Required` `String` | - |
| target | `Required` `String` | - |
| project_id | `Optional` `Integer` | - |
| whois_notifications | `Optional` `Array` | Notification handler ids |
| whois_notifications_timing | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `7`,  `14`,  `30`,  `60`  (days) |
| ssl_notifications | `Optional` `Array` | Notification handler ids |
| ssl_notifications_timing | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `7`,  `14`,  `30`,  `60`  (days) |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/domain-names' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
--form 'target=example.com' \  
```
**Response example**

```json
{
  "data": {
    "id": 1
  }
}
```

### Update domain name monitor

**Endpoint**
*POST*  `https://app.hydrozen.io/api/domain-names/{domain_name_id}`


| Parameters | Details | Description |  
|--|--|--|
| name | `Required` `String` | - |
| target | `Required` `String` | - |
| project_id | `Optional` `Integer` | - |
| whois_notifications | `Optional` `Array` | Notification handler ids |
| whois_notifications_timing | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `7`,  `14`,  `30`,  `60`  (days) |
| ssl_notifications | `Optional` `Array` | Notification handler ids |
| ssl_notifications_timing | `Optional` `Integer` | Allowed values:  `1`,  `2`,  `3`,  `7`,  `14`,  `30`,  `60`  (days) |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/domain-names/{domain_name_id}' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
```
**Response example**
```json
{
  "data": {
    "id": 1
  }
}
```

### Delete domain name monitor

**Endpoint**
*DELETE*  `https://app.hydrozen.io/api/domain-names/{domain_name_id}`

**Example**
```bash
curl --request DELETE \  
--url 'https://app.hydrozen.io/api/domain-names/{domain_name_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```
## Notification handlers

### Retrieve all notification handlers
**Endpoint**
*GET*  `https://app.hydrozen.io/api/notification-handler/`

**Example**
```bash
curl --request GET \  
--url 'https://app.hydrozen.io/api/notification-handler/' \  
--header 'Authorization: Bearer  {api_key}' \
```
| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to  `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are:  `10`  ,  `25`  ,  `50`  ,  `100`  ,  `250`  ,  `500`  ,  `1000`. Defaults to  `25`. |

**Response example**
```json
{
  "data": [
    {
      "id": 1,
      "type": "email",
      "name": "Work email",
      "settings": {
        "email": "hey@example.com"
      },
      "is_enabled": true,
      "last_datetime": null,
      "datetime": "2021-06-27 22:16:23"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/notification-handler?&page=1",
    "last": "https://app.hydrozen.io/api/notification-handler?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/notification-handler?&page=1"
  }
}
```

### Retrieve one notification handler

**Endpoint**
*GET*  `https://app.hydrozen.io/api/notification-handler/{notification_handler_id}`

**Example**
```bash
curl --request GET \  
--url 'https://app.hydrozen.io/api/notification-handler/{notification_handler_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```

**Response example**
```json
{
  "data": {
    "id": 1,
    "type": "email",
    "name": "Work email",
    "settings": {
      "email": "hey@example.com"
    },
    "is_enabled": true,
    "last_datetime": null,
    "datetime": "2021-06-27 22:16:23"
  }
}
```

### Create notification handler

**Endpoint**
*POST*  `https://app.hydrozen.io/api/notification-handlers`

| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| type | `Required` `String` | Allowed values:  `email`  ,  `webhook`  ,  `squadcast`  ,  `googlechat`  ,  `slack`  ,  `discord`  ,  `telegram`  ,  `microsoft_teams` |
| email | `Optional` `String` | Email address, applicable when:  `type = email`,  Email |
| webhook | `Optional` `String` | Webhook URL, applicable when:  `type = webhook` |
| squadcast | `Optional` `String` | Squadcast webhook URL, applicable when:  `type = squadcast` |
| googlechat | `Optional` `String` | Google Chat webhook URL, applicable when:  `type = googlechat` |
| slack | `Optional` `String` | Slack webhook URL, applicable when:  `type = slack` |
| discord | `Optional` `String` | Discord webhook URL, applicable when:  `type = discord` |
| telegram | `Optional` `String` | Telegram API Token, applicable when:  `type = telegram` |
| telegram_chat_id | `Optional` `String` | Telegram Chat ID, applicable when:  `type = telegram` |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/notification-handlers' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example' \  
--form 'type=email' \  
--form 'email=hello@example.com' \  
```
**Response example**
```json
{
  "data": {
    "id": 1
  }
}
```

### Update notification handler

**Endpoint**
*POST*  `https://app.hydrozen.io/api/notification-handlers/{notification_handler_id}`


| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |
| type | `Required` `String` | Allowed values:  `email`  ,  `webhook`  ,  `squadcast`  ,  `googlechat`  ,  `slack`  ,  `discord`  ,  `telegram`  ,  `microsoft_teams` |
| email | `Optional` `String` | Email address, applicable when:  `type = email`,  Email |
| webhook | `Optional` `String` | Webhook URL, applicable when:  `type = webhook` |
| squadcast | `Optional` `String` | Squadcast webhook URL, applicable when:  `type = squadcast` |
| googlechat | `Optional` `String` | Google Chat webhook URL, applicable when:  `type = googlechat` |
| slack | `Optional` `String` | Slack webhook URL, applicable when:  `type = slack` |
| discord | `Optional` `String` | Discord webhook URL, applicable when:  `type = discord` |
| telegram | `Optional` `String` | Telegram API Token, applicable when:  `type = telegram` |
| telegram_chat_id | `Optional` `String` | Telegram Chat ID, applicable when:  `type = telegram` |
| is_enabled | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \  
--url 'https://app.hydrozen.io/api/notification-handlers/{notification_handler_id}' \  
--header 'Authorization: Bearer  {api_key}' \  
--header 'Content-Type: multipart/form-data' \  
--form 'name=Example new name' \  
--form 'is_enabled=1' \  
```
**Response example**
```json
{
  "data": {
    "id": 1
  }
}
```

### Delete notification handler

**Endpoint**

*DELETE*  `https://app.hydrozen.io/api/notification-handlers/{notification_handler_id}`

**Example**
```bash
curl --request DELETE \  
--url 'https://app.hydrozen.io/api/notification-handlers/{notification_handler_id}' \  
--header 'Authorization: Bearer  {api_key}' \
```


## User

### Retrieve one user

**Endpoint**

*GET* `https://app.hydrozen.io/api/user`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/user' \
--header 'Authorization: Bearer {api_key}'
```

**Response example**

```json
{
  "data": {
    "id": "1",
    "type": "users",
    "email": "example@example.com",
    "billing": {
      "type": "personal",
      "name": "John Doe",
      "address": "Lorem Ipsum",
      "city": "Dolor Sit",
      "county": "Amet",
      "zip": "5000",
      "country": "",
      "phone": "",
      "tax_id": ""
    },
    "is_enabled": true,
    "plan_id": "custom",
    "plan_expiration_date": "2025-12-12 00:00:00",
    "plan_settings": {},
    "plan_trial_done": false,
    "language": "english",
    "timezone": "UTC",
    "country": null,
    "date": "2020-01-01 00:00:00",
    "last_activity": "2020-01-01 00:00:00",
    "total_logins": 10
  }
}
```

## Server Monitors

### Retrieve all server monitors

**Endpoint**

*GET* `https://app.hydrozen.io/api/server-monitors/`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/server-monitors/' \
--header 'Authorization: Bearer {api_key}'
```

| Parameters | Details | Description |
|------------|----------|-------------|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | Allowed values: `10`, `25`, `50`, `100`, `250`, `500`, `1000`. Defaults to `25`. |

**Response example**
```json
{
  "data": [
    {
      "id": 1,
      "project_id": 0,
      "name": "Sample",
      "target": "123.123.123.123",
      "settings": {
        "server_check_interval_seconds": 60
      },
      "cpu_usage": 0.7,
      "ram_usage": 30.65,
      "disk_usage": 16.49,
      "cpu_load_1": 0,
      "cpu_load_5": 0,
      "cpu_load_15": 0,
      "is_enabled": true,
      "total_logs": 100,
      "last_log_datetime": "2024-01-14 02:45:05",
      "datetime": "2024-01-12 02:17:06",
      "last_datetime": "2024-01-14 03:03:35"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/server-monitors?&page=1",
    "last": "https://app.hydrozen.io/api/server-monitors?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/server-monitors?&page=1"
  }
}
```

### Retrieve one server monitor

**Endpoint**

*GET* `https://app.hydrozen.io/api/server-monitors/{server_monitor_id}`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/server-monitors/{server_monitor_id}' \
--header 'Authorization: Bearer {api_key}'
```

**Response example**
```json
{
  "data": {
    "id": 1,
    "project_id": 0,
    "name": "Sample",
    "target": "123.123.123.123",
    "settings": {
      "server_check_interval_seconds": 60
    },
    "cpu_usage": 0.7,
    "ram_usage": 30.65,
    "disk_usage": 16.49,
    "cpu_load_1": 0,
    "cpu_load_5": 0,
    "cpu_load_15": 0,
    "is_enabled": true,
    "total_logs": 100,
    "last_log_datetime": "2024-01-14 02:45:05",
    "datetime": "2024-01-12 02:17:06",
    "last_datetime": "2024-01-14 03:03:35"
  }
}
```

### Delete server monitor

**Endpoint**

*DELETE* `https://app.hydrozen.io/api/server-monitors/{server_monitor_id}`

**Example**
```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/server-monitors/{server_monitor_id}' \
--header 'Authorization: Bearer {api_key}'
```
## Projects

### Retrieve all projects
*GET* `/api/projects/`

 **Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/projects/' \
--header 'Authorization: Bearer {api_key}'
```

**Response**

```json
{
  "data": [
    {
      "id": 1,
      "name": "Development",
      "color": "#0e23cc",
      "last_datetime": "2021-03-14 21:22:37",
      "datetime": "2021-02-04 17:51:07"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/projects?page=1",
    "last": "https://app.hydrozen.io/api/projects?page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/projects?page=1"
  }
}
```
### Retrieve one project

*GET* `/api/projects/{project_id}`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response**

```json
{
    "data": {
        "id": 1,
        "name": "Development",
        "color": "#0e23cc",
        "last_datetime": "2021-03-14 21:22:37",
        "datetime": "2021-02-04 17:51:07"
    }
}
```
### Create Project

*POST* `/api/projects`

**Example**

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/projects' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=Production' \
--form 'color=#ffffff' \
```

**Response**

```json
{
    "data": {
        "id": 1
    }
}
```
### Update Project

*POST* `/api/projects/{project_id}`

**Example**

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=Production' \
--form 'color=#000000' \
```

**Response**
```json
{
  "data": {
    "id": 1
  }
}
```
### Delete Project

*DELETE* `/api/projects/{project_id}`

**Example**

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
```

## Status Pages

### Retrieve all status pages

*GET* `/api/status-pages/`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/status-pages/' \
--header 'Authorization: Bearer {api_key}' \
```

**Response**

```json
{
  "data": [
    {
      "id": 1,
      "domain_id": 0,
      "monitors_ids": [1, 2, 3],
      "project_id": 0,
      "url": "example",
      "full_url": "https://app.hydrozen.io/s/example/",
      "name": "Example",
      "description": "This is just a simple description for the example status page 👋.",
      "socials": {
        "facebook": "example",
        "instagram": "example",
        "twitter": "example",
        "email": "",
        "website": "https://example.com/"
      },
      "logo_url": "",
      "favicon_url": "",
      "password": false,
      "timezone": "UTC",
      "custom_js": "",
      "custom_css": "",
      "pageviews": 50,
      "is_se_visible": true,
      "is_removed_branding": false,
      "is_enabled": true,
      "datetime": "2021-02-16 10:47:34"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/status-pages?&page=1",
    "last": "https://app.hydrozen.io/api/status-pages?&page=1",
    "next": null,
    "prev": null,
    "self": "https://app.hydrozen.io/api/status-pages?&page=1"
  }
}
```
### Retrieve one status page

*GET* `/api/status-pages/{status_page_id}`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/status-pages/{status_page_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response**

```json
{
  "data": {
    "id": 1,
    "domain_id": 0,
    "monitors_ids": [1, 2, 3],
    "project_id": 0,
    "url": "example",
    "full_url": "https://app.hydrozen.io/s/example/",
    "name": "Example",
    "description": "This is just a simple description for the example status page 👋.",
    "socials": {
      "facebook": "example",
      "instagram": "example",
      "twitter": "example",
      "email": "",
      "website": "https://example.com/"
    },
    "logo_url": "",
    "favicon_url": "",
    "password": false,
    "timezone": "UTC",
    "custom_js": "",
    "custom_css": "",
    "pageviews": 50,
    "is_se_visible": true,
    "is_removed_branding": false,
    "is_enabled": true,
    "datetime": "2021-02-16 10:47:34"
  }
}
```

## Custom Domains

### Retrieve all custom domains
*GET* `/api/domains/`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/domains/' \
--header 'Authorization: Bearer {api_key}' \
```

**Response**

```json
{
    "data": [
        {
            "id": 1,
            "scheme": "https://",
            "host": "example.com",
            "custom_index_url": "",
            "is_enabled": true,
            "last_datetime": null,
            "datetime": "2021-02-04 23:29:18"
        }
    ],
    "meta": {
        "page": 1,
        "results_per_page": 25,
        "total": 1,
        "total_pages": 1
    },
    "links": {
        "first": "https://app.hydrozen.io/api/domains?&page=1",
        "last": "https://app.hydrozen.io/api/domains?&page=1",
        "next": null,
        "prev": null,
        "self": "https://app.hydrozen.io/api/domains?&page=1"
    }
}
```

### Retrieve one custom domain

*GET* `/api/domains/{domain_id}`

** Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response**

```json
{
    "data": {
        "id": 1,
        "scheme": "https://",
        "host": "example.com",
        "custom_index_url": "",
        "is_enabled": true,
        "last_datetime": null,
        "datetime": "2021-02-04 23:29:18"
    }
}
```

### Create custom domain

*POST* `/api/domains`

**Example**

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/domains' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'host=domain.com' \
--form 'custom_index_url=https://mywebsite.com/' \
--form 'custom_not_found_url=https://mywebsite.com/404-page'
```

**Response**

```json
{
    "data": {
        "id": 1
    }
}
```

### Update custom domain

*POST* `/api/domains/{domain_id}`

**Example**

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'host=domain.com' \
```

**Response**

```json
{
  "data": {
    "id": 1
  }
}
```

### Delete custom domain

*DELETE* `/api/domains/{domain_id}`

**Example**

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
```

## DNS monitors

### Retrieve all DNS monitors

**Endpoint**

*GET* `https://app.hydrozen.io/api/dns-monitors`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/dns-monitors' \
--header 'Authorization: Bearer {api_key}'
```

**Response example**

```json

{
  "data": [
    {
      "id": 1,
      "project_id": 0,
      "name": "Sample",
      "target": "example.com",
      "dns": {
        "A": [
          {
            "host": "example.com",
            "ip": "12.12.12.12"
          }
        ],
        "CNAME": [],
        "HINFO": [],
        "CAA": [],
        "MX": []
      },
      "notifications": [1],
      "settings": {
        "dns_check_interval_seconds": 300
      },
      "total_checks": 1,
      "total_changes": 0,
      "last_check_datetime": "2024-01-03 01:48:42",
      "next_check_datetime": "2024-01-03 01:49:13",
      "last_change_datetime": null,
      "is_enabled": true,
      "datetime": "2023-12-31 03:54:09",
      "last_datetime": "2024-01-03 00:16:36"
    }
  ],
  "meta": {
    "page": 1,
    "results_per_page": 25,
    "total": 1,
    "total_pages": 1
  },
  "links": {
    "first": "https://app.hydrozen.io/api/dns-monitors?page=1",
    "last": "https://app.hydrozen.io/api/dns-monitors?page=1",
    "next": null,
    "prev": null
  }
}

```

### Retrieve one DNS monitor

**Endpoint**

*GET* `https://app.hydrozen.io/api/dns-monitors/{id}`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/dns-monitors/{id}' \
--header 'Authorization: Bearer {api_key}'
```
**Response example**

```json
{
  "data": {
    "id": 1,
    "project_id": 0,
    "name": "Sample",
    "target": "example.com",
    "dns": {
      "A": [
        {
          "host": "example.com",
          "ip": "12.12.12.12"
        }
      ],
      "CNAME": [],
      "HINFO": [],
      "CAA": [],
      "MX": []
    },
    "notifications": [1],
    "settings": {
      "dns_check_interval_seconds": 300
    },
    "total_checks": 1,
    "total_changes": 0,
    "last_check_datetime": "2024-01-03 01:48:42",
    "next_check_datetime": "2024-01-03 01:49:13",
    "last_change_datetime": null,
    "is_enabled": true,
    "datetime": "2023-12-31 03:54:09",
    "last_datetime": "2024-01-03 00:16:36"
  }
}
```

### Delete DNS monitor

**Endpoint**

*DELETE* `https://app.hydrozen.io/api/dns-monitors/{id}`

**Example**

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/dns-monitors/{id}' \
--header 'Authorization: Bearer {api_key}'
**Response example**

```json
{
  "message": "DNS monitor deleted successfully"
}
```

## Teams member

### Retrieve all teams members

**Endpoint**

*GET*  `https://app.hydrozen.io/api/teams-member/`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/teams-member/' \
--header 'Authorization: Bearer {api_key}' \
```

| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |

**Response example**
```json
{
    "data": [
        {
            "id": 1,
            "access": {
                "read": true,
                "create": true,
                "update": true,
                "delete": false
            },
            "status": 1,
            "last_datetime": "2022-06-07 13:04:31",
            "datetime": "2022-06-05 14:37:10",
            "team_id": 1,
            "name": "Example team"
        }
    ],
    "meta": {
        "page": 1,
        "results_per_page": 25,
        "total": 1,
        "total_pages": 1
    },
    "links": {
        "first": "https://app.hydrozen.io/api/teams-member?&page=1",
        "last": "https://app.hydrozen.io/api/teams-member?&page=1",
        "next": null,
        "prev": null,
        "self": "https://app.hydrozen.io/api/teams-member?&page=1"
    }
}
```

### Retrieve one teams member

**Endpoint**

*GET*  `https://app.hydrozen.io/api/teams-member/{team_member_id}`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/teams-member/{team_member_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response example**
```json
{
    "data": {
        "id": 1,
        "access": {
            "read": true,
            "create": true,
            "update": true,
            "delete": false
        },
        "status": 1,
        "last_datetime": "2022-06-07 13:04:31",
        "datetime": "2022-06-05 14:37:10",
        "team_id": 1,
        "name": "Example team"
    }
}
```

### Update teams member

**Endpoint**

*POST*  `https://app.hydrozen.io/api/teams-member/{team_member_id}`

| Parameters | Details | Description |
|--|--|--|
| status | `Optional` `Boolean` | - |

**Example**
```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/teams-member/{team_member_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'status=1' \
```

**Response example**
```json
{
    "data": {
        "id": 1
    }
}
```

### Delete teams member

**Endpoint**

*DELETE*  `https://app.hydrozen.io/api/teams-member/{team_member_id}`

**Example**
```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/teams-member/{team_member_id}' \
--header 'Authorization: Bearer {api_key}' \
```

## Payments

### Retrieve all payments

**Endpoint**

*GET*  `https://app.hydrozen.io/api/payments/`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/payments/' \
--header 'Authorization: Bearer {api_key}' \
```

| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |

**Response example**
```json
{
    "data": [
        {
            "id": 1,
            "plan_id": 1,
            "processor": "stripe",
            "type": "one_time",
            "frequency": "monthly",
            "email": "example@example.com",
            "name": null,
            "total_amount": "4.99",
            "currency": "USD",
            "status": true,
            "date": "2021-03-25 15:08:58"
        }
    ],
    "meta": {
        "page": 1,
        "results_per_page": 25,
        "total": 1,
        "total_pages": 1
    },
    "links": {
        "first": "https://app.hydrozen.io/api/payments?&page=1",
        "last": "https://app.hydrozen.io/api/payments?&page=1",
        "next": null,
        "prev": null,
        "self": "https://app.hydrozen.io/api/payments?&page=1"
    }
}
```

### Retrieve one payment

**Endpoint**

*GET*  `https://app.hydrozen.io/api/payments/{payment_id}`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/payments/{payment_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response example**
```json
{
    "data": {
        "id": 1,
        "plan_id": 1,
        "processor": "stripe",
        "type": "one_time",
        "frequency": "monthly",
        "email": "example@example.com",
        "name": null,
        "total_amount": "4.99",
        "currency": "USD",
        "status": true,
        "date": "2021-03-25 15:08:58"
    }
}
```

## Logs

### Retrieve all logs

**Endpoint**

*GET*  `https://app.hydrozen.io/api/logs/`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/logs/' \
--header 'Authorization: Bearer {api_key}' \
```

| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |

**Response example**
```json
{
    "data": [
        {
            "type": "login.success",
            "ip": "127.0.0.1",
            "device_type": "mobile",
            "continent_code": "EU",
            "country_code": "IT",
            "city_name": "Rome",
            "datetime": "2021-02-03 12:21:40"
        }
    ],
    "meta": {
        "page": 1,
        "results_per_page": 25,
        "total": 1,
        "total_pages": 1
    },
    "links": {
        "first": "https://app.hydrozen.io/api/logs?&page=1",
        "last": "https://app.hydrozen.io/api/logs?&page=1",
        "next": null,
        "prev": null,
        "self": "https://app.hydrozen.io/api/logs?&page=1"
    }
}
```
## Status Page Statistics

### Retrieve one status page statistics

**Endpoint**

*GET*  `https://app.hydrozen.io/api/statistics/{status_page_id}`

| Parameters | Details | Description |
|--|--|--|
| start_date | `Required` `String` | Start date in `Y-m-d` format. |
| end_date | `Required` `String` | End date in `Y-m-d` format. |
| type | `Optional` `String` | Type of data to be returned. Allowed values are: `overview`, `referrer_host`, `referrer_path`, `country_code`, `city_name`, `os_name`, `browser_name`, `device_type`, `browser_language`, `utm_source`, `utm_medium`, `utm_campaign`. Defaults to `overview`. |
| country_code | `Optional` `String` | Parameter only available for the `city_name` type. |
| utm_source | `Optional` `String` | Parameter only available for the `utm_medium` and `utm_campaign` type. |
| utm_medium | `Optional` `String` | Parameter only available for the `utm_campaign` type. |

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/statistics/{status_page_id}?start_date=2020-01-01&end_date=2021-01-01' \
--header 'Authorization: Bearer {api_key}' \
```

**Response example**
```json
{
    "data": [
        {
            "pageviews": 20,
            "visitors": 5,
            "formatted_date": "2021-01"
        },
        {
            "pageviews": 35,
            "visitors": 10,
            "formatted_date": "2021-02"
        },
        {
            "pageviews": 50,
            "visitors": 25,
            "formatted_date": "2021-03"
        }
    ]
}
```

## Teams

### Retrieve all teams

**Endpoint**

*GET*  `https://app.hydrozen.io/api/teams/`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/teams/' \
--header 'Authorization: Bearer {api_key}' \
```

| Parameters | Details | Description |
|--|--|--|
| page | `Optional` `Integer` | The page number that you want results from. Defaults to `1`. |
| results_per_page | `Optional` `Integer` | How many results you want per page. Allowed values are: `10` , `25` , `50` , `100` , `250` , `500` , `1000`. Defaults to `25`. |

**Response example**
```json
{
    "data": [
        {
            "id": 1,
            "name": "Example team",
            "team_members": [
                {
                    "team_member_id": 1,
                    "user_email": "hello@example.com",
                    "access": {
                        "read": true,
                        "create": true,
                        "update": true,
                        "delete": false
                    },
                    "status": 1,
                    "datetime": "2022-06-05 14:37:10",
                    "last_datetime": "2022-06-07 13:04:31"
                }
            ],
            "last_datetime": null,
            "datetime": "2022-04-05 21:08:52"
        }
    ],
    "meta": {
        "page": 1,
        "results_per_page": 25,
        "total": 1,
        "total_pages": 1
    },
    "links": {
        "first": "https://app.hydrozen.io/api/teams?&page=1",
        "last": "https://app.hydrozen.io/api/teams?&page=1",
        "next": null,
        "prev": null,
        "self": "https://app.hydrozen.io/api/teams?&page=1"
    }
}
```

---

### Retrieve one team

**Endpoint**

*GET*  `https://app.hydrozen.io/api/teams/{team_id}`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/teams/{team_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response example**
```json
{
    "data": {
        "id": 1,
        "name": "Example team",
        "team_members": [
            {
                "team_member_id": 1,
                "user_email": "hello@example.com",
                "access": {
                    "read": true,
                    "create": true,
                    "update": true,
                    "delete": false
                },
                "status": 1,
                "datetime": "2022-06-05 14:37:10",
                "last_datetime": "2022-06-07 13:04:31"
            }
        ],
        "last_datetime": null,
        "datetime": "2022-04-05 21:08:52"
    }
}
```

---

### Create team

**Endpoint**

*POST*  `https://app.hydrozen.io/api/teams`

| Parameters | Details | Description |
|--|--|--|
| name | `Required` `String` | - |

**Example**
```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/teams' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=My team' \
```

**Response example**
```json
{
    "data": {
        "id": 1
    }
}
```

---

### Update team

**Endpoint**

*POST*  `https://app.hydrozen.io/api/teams/{team_id}`

| Parameters | Details | Description |
|--|--|--|
| name | `Optional` `String` | - |

**Example**
```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/teams/{team_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=My new team name' \
```

**Response example**
```json
{
    "data": {
        "id": 1
    }
}
```

---

### Delete team

**Endpoint**

*DELETE*  `https://app.hydrozen.io/api/teams/{team_id}`

**Example**
```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/teams/{team_id}' \
--header 'Authorization: Bearer {api_key}' \
```

## Team Members

### Retrieve team members

**Endpoint**

*GET*  `https://app.hydrozen.io/api/team-members/{team_id}`

**Example**
```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/team-members/{team_id}' \
--header 'Authorization: Bearer {api_key}' \
```

**Response example**
```json
{
    "data": [
        {
            "id": 1,
            "team_id": 1,
            "user_email": "hello@example.com",
            "access": {
                "read": true,
                "create": true,
                "update": true,
                "delete": false
            },
            "status": 1,
            "datetime": "2022-06-05 14:37:10",
            "last_datetime": "2022-06-07 13:04:31"
        }
    ]
}
```

---

### Create team member

**Endpoint**

*POST*  `https://app.hydrozen.io/api/team-members`

| Parameters | Details | Description |
|--|--|--|
| team_id | `Required` `Integer` | - |
| user_email | `Required` `String` | - |
| access | `Optional` `String Array` | Allowed values:<br><br>`read.all`<br><br>`create.notification_handlers`, `create.projects`, `create.domains`, `create.status_pages`, `create.monitors`, `create.domain_names`, `create.heartbeats`, `create.dns_monitors`, `create.server_monitors`<br><br>`update.notification_handlers`, `update.projects`, `update.domains`, `update.status_pages`, `update.monitors`, `update.domain_names`, `update.heartbeats`, `update.dns_monitors`, `update.server_monitors`<br><br>`delete.projects`, `delete.notification_handlers`, `delete.domains`, `delete.status_pages`, `delete.monitors`, `delete.domain_names`, `delete.heartbeats`, `delete.dns_monitors`, `delete.server_monitors` |

**Example**
```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/team-members' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'team_id=1' \
--form 'user_email=hello@example.com' \
```

**Response example**
```json
{
    "data": {
        "id": 1
    }
}
```

---

### Update team member

**Endpoint**

*POST*  `https://app.hydrozen.io/api/team-members/{team_member_id}`

| Parameters | Details | Description |
|--|--|--|
| access | `Optional` `String Array` | Allowed values:<br><br>`read.all`<br><br>`create.notification_handlers`, `create.projects`, `create.domains`, `create.status_pages`, `create.monitors`, `create.domain_names`, `create.heartbeats`, `create.dns_monitors`, `create.server_monitors`<br><br>`update.notification_handlers`, `update.projects`, `update.domains`, `update.status_pages`, `update.monitors`, `update.domain_names`, `update.heartbeats`, `update.dns_monitors`, `update.server_monitors`<br><br>`delete.projects`, `delete.notification_handlers`, `delete.domains`, `delete.status_pages`, `delete.monitors`, `delete.domain_names`, `delete.heartbeats`, `delete.dns_monitors`, `delete.server_monitors` |

**Example**
```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/team-members/{team_member_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'access[]=create.projects' \
--form 'access[]=update.projects' \
```

**Response example**
```json
{
    "data": {
        "id": 1
    }
}
```

---

### Delete team member

**Endpoint**

*DELETE*  `https://app.hydrozen.io/api/team-members/{team_member_id}`

**Example**
```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/team-members/{team_member_id}' \
--header 'Authorization: Bearer {api_key}' \
```
