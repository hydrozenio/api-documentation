# Hydrozen.io API Documentation

This is the documentation for the available API endpoints, which are built around the REST architecture. All the API endpoints will return a JSON response with the standard HTTP response codes and require Bearer Authentication via an API Key.

---

## Table of Contents

- [Base URL](#base-url)
- [Authentication](#authentication)

- [Teams member](#teams-member)
	- [Retrieve All](#retrieve-all-teams-members)
	- [Retrieve one](#retrieve-one-teams-member)
	- [Update](#update-teams-member)
	- [Delete](#delete-teams-member)

- [Payments](#payments)
	- [Retrieve All](#retrieve-all-payments)
	- [Retrieve one](#retrieve-one-payment)

- [Logs](#logs)
	- [Retrieve All](#retrieve-all-logs)

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

---

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

---

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

---

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

---

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
