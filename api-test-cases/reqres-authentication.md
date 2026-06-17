# API Test Cases — ReqRes (Authentication & Users)

**Base URL:** `https://reqres.in/api`

---

### API_AUTH_001 — Successful login

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/login` |
| **Priority** | High |

**Request Body:**
```json
{
  "email": "eve.holt@reqres.in",
  "password": "cityslicka"
}
```

**Expected Response:**
- Status code: `200 OK`
- Response contains a `token` field
- Token is a non-empty string

---

### API_AUTH_002 — Login with missing password

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/login` |
| **Priority** | High |

**Request Body:**
```json
{
  "email": "eve.holt@reqres.in"
}
```

**Expected Response:**
- Status code: `400 Bad Request`
- Response contains `error`: "Missing password"

---

### API_AUTH_003 — Successful registration

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/register` |
| **Priority** | High |

**Request Body:**
```json
{
  "email": "eve.holt@reqres.in",
  "password": "pistol"
}
```

**Expected Response:**
- Status code: `200 OK`
- Response contains `id` and `token`

---

### API_AUTH_004 — Registration with missing fields

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/register` |
| **Priority** | Medium |

**Request Body:**
```json
{
  "email": "sydney@fife"
}
```

**Expected Response:**
- Status code: `400 Bad Request`
- Response contains `error`: "Missing password"

---

### API_AUTH_005 — Get a single user

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/users/2` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `200 OK`
- Response `data` object contains `id`, `email`, `first_name`, `last_name`

---

### API_AUTH_006 — Get a non-existent user

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/users/999` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `404 Not Found`
- Response body is empty
