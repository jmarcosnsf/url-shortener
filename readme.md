# url-shortener

A simple URL shortener API built with Go and Redis.

## Overview

This project is a learning exercise exploring REST APIs, routing, and data persistence with Redis in Go.

## Requirements

- Go 1.22+
- Docker (for Redis)

## Running

Start Redis:

```bash
docker compose up -d
```

Run the API:

```bash
go run cmd/api/main.go
```

The server starts on port `8080`.

## API

### Shorten a URL

```
POST /api/url/shorten
Content-Type: application/json

{
  "url": "https://example.com/some/long/path"
}
```

**Response (201 Created):**

```json
{
  "data": {
    "code": "xK9mZ2pL"
  }
}
```

### Get original URL

```
GET /api/url/{code}
```

**Response (200 OK):**

```json
{
  "data": {
    "full_url": "https://example.com/some/long/path"
  }
}
```

**Response (404 Not Found):**

```json
{
  "error": "url not found"
}
```

## Dependencies

- [chi](https://github.com/go-chi/chi) — lightweight router
- [go-redis](https://github.com/redis/go-redis) — Redis client