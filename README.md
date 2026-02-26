
# Hydrozen.io API Documentation

This is the documentation for the available API endpoints, which are built around the REST architecture. All the API endpoints will return a JSON response with the standard HTTP response codes and need a Bearer Authentication via an API Key.

## Table of Contents

-  [Base URL](#base-url)
-  [Authentication](#authentication)
-  [Uptime Monitors](#uptime-monitors)
	- [Retrieve All](#retrieve-all-uptime-monitors)
	- [Retrieve one](#retrieve-one-uptime-monitor)
	- [Create](#create-uptime-monitor)
	- [Update](#update-uptime-monitor)
	- [Delete](#delete-uptime-monitor)
-  [Heartbeat Monitors](#heartbeat-monitors)
	- [Retrieve All](#retrieve-all-heartbeat-monitors)
	- [Retrieve one](#retrieve-one-heartbeat-monitor)
	- [Create](#create-heartbeat-monitor)
	- [Update](#update-heartbeat-monitor)
	- [Delete](#delete-heartbeat-monitor)
-  [Domain name Monitors](#domain-name-monitors)
	- [Retrieve All](#retrieve-all-domain-name-monitors)
	- [Retrieve one](#retrieve-one-domain-name-monitor)
	- [Create](#create-domain-name-monitor)
	- [Update](#update-domain-name-monitor)
	- [Delete](#delete-domain-name-monitor)
-  [Notification Handlers](#notification-handlers)
	- [Retrieve All](#retrieve-all-notification-handlers)
	- [Retrieve one](#retrieve-one-notification-handler)
	- [Create](#create-notification-handler)
	- [Update](#update-notification-handler)
	- [Delete](#delete-notification-handler)
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

### Retrieve one

**Endpoint**

*GET* `https://app.hydrozen.io/api/user`

**Example**

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/user' \
--header 'Authorization: Bearer {api_key}'

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

### Retrieve all
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
### Retrieve one

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
### Create

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
### Update

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
### Delete

*DELETE* `/api/projects/{project_id}`

**Example**

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
```

## Status Pages

### Retrieve all

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
### Retrieve one

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

### Retrieve all
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

### Retrieve one

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

### Create

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

### Update

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

### Delete

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
