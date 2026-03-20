# url-shortener

A simple URL shortener API built with Go.

## Overview

This project is a learning exercise exploring REST APIs, routing, and data handling in Go. Currently uses in-memory storage (map) for simplicity.

## Requirements

- Go 1.22+

## Running
```bash
go run main.go
```

The server starts on port `8080`.

## API

### Shorten a URL
```
POST /api/shortener
Content-Type: application/json

{
  "url": "https://example.com/some/long/path"
}
```

**Response (201 Created):**
```json
{
  "data": "xK9mZ2pL"
}
```

### Redirect
```
GET /{code}
```

Redirects to the original URL (HTTP 308).

**Example:** `GET /xK9mZ2pL` → redirects to `https://example.com/some/long/path`

## Dependencies

- [chi](https://github.com/go-chi/chi) — lightweight router

## Roadmap

- [ ] Database integration (replace in-memory map)
- [ ] Improve code generation (collision handling, uniqueness guarantees)
- [ ] Refactor project structure (separate layers/packages)