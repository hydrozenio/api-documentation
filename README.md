# Hydrozen.io API Documentation

This is the documentation for the available API endpoints, which are built around the REST architecture. All the API endpoints will return a JSON response with the standard HTTP response codes and require Bearer Authentication via an API Key.

---

- [Base URL](#base-url)
- [Authentication](#authentication)
- [Status Page Statistics](#status-page-statistics)
	- [Retrieve one](#retrieve-one-status-page-statistics)
- [Teams](#teams)
	- [Retrieve all](#retrieve-all-teams)
	- [Retrieve one](#retrieve-one-team)
	- [Create](#create-team)
	- [Update](#update-team)
	- [Delete](#delete-team)
- [Team Members](#team-members)
	- [Retrieve](#retrieve-team-members)
	- [Create](#create-team-member)
	- [Update](#update-team-member)
	- [Delete](#delete-team-member)

---


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
