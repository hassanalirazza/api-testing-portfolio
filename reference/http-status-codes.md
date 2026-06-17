# HTTP Status Codes — QA Reference

A quick reference for the status codes most relevant to API testing, with what a tester should verify for each.

---

## 2xx — Success

| Code | Meaning | When to expect it |
|---|---|---|
| 200 | OK | Successful GET, PUT, or PATCH |
| 201 | Created | Successful POST that creates a resource |
| 204 | No Content | Successful request with no response body (often DELETE) |

## 3xx — Redirection

| Code | Meaning | When to expect it |
|---|---|---|
| 301 | Moved Permanently | Resource has a new permanent URL |
| 302 | Found | Temporary redirect |
| 304 | Not Modified | Cached version is still valid |

## 4xx — Client Errors

| Code | Meaning | When to expect it |
|---|---|---|
| 400 | Bad Request | Invalid or malformed request body |
| 401 | Unauthorized | Missing or invalid authentication |
| 403 | Forbidden | Authenticated but not allowed |
| 404 | Not Found | Resource does not exist |
| 405 | Method Not Allowed | HTTP method not supported on endpoint |
| 409 | Conflict | Duplicate or conflicting resource state |
| 422 | Unprocessable Entity | Validation failed on the request data |
| 429 | Too Many Requests | Rate limit exceeded |

## 5xx — Server Errors

| Code | Meaning | When to expect it |
|---|---|---|
| 500 | Internal Server Error | Unhandled server-side failure |
| 502 | Bad Gateway | Invalid response from upstream server |
| 503 | Service Unavailable | Server overloaded or down for maintenance |
| 504 | Gateway Timeout | Upstream server did not respond in time |

---

## Tester's Note

A key part of API testing is **negative testing** — deliberately sending invalid requests to confirm the API returns the correct 4xx code with a clear error message, rather than failing silently or returning 200.
