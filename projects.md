# Projects

## Retrieve all
`GET /api/projects/`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/projects/' \
--header 'Authorization: Bearer {api_key}'
```

### Response

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
## Retrieve one

`GET /api/projects/{project_id}`

### Example

```bash
curl --request GET \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
```

### Response

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
## Create

`POST /api/projects`

### Example

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/projects' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=Production' \
--form 'color=#ffffff' \
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

`POST /api/projects/{project_id}`

### Example

```bash
curl --request POST \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
--header 'Content-Type: multipart/form-data' \
--form 'name=Production' \
--form 'color=#000000' \
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

`DELETE /api/projects/{project_id}`

### Example

```bash
curl --request DELETE \
--url 'https://app.hydrozen.io/api/projects/{project_id}' \
--header 'Authorization: Bearer {api_key}' \
```
