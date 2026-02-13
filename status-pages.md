# Status Pages

## Retrieve all
`GET /api/status-pages/`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/status-pages/' \
--header 'Authorization: Bearer {api_key}' \
```

### Response

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
## Retrieve one

`GET /api/status-pages/{status_page_id}`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/status-pages/{status_page_id}' \
--header 'Authorization: Bearer {api_key}' \
```

### Response

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
