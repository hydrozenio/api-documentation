# Custom Domains

## Retrieve all
`GET /api/domains/`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/domains/' \
--header 'Authorization: Bearer {api_key}' \
```

### Response

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

## Retrieve one

`GET /api/domains/{domain_id}`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
```

### Response

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

## Create

`POST /api/domains`

### Example

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/domains' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'host=domain.com' \
--form 'custom_index_url=https://mywebsite.com/' \
--form 'custom_not_found_url=https://mywebsite.com/404-page'
```

### Response

```json
{
    "data": {
        "id": 1
    }
}
```

## Update

`POST /api/domains/{domain_id}`

### Example

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'host=domain.com' \
```

### Response

```json
{
  "data": {
    "id": 1
  }
}
```

## Delete

`DELETE /api/domains/{domain_id}`

### Example

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/domains/{domain_id}' \
--header 'Authorization: Bearer {api_key}' \
```
