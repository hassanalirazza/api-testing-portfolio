# API Test Cases — Restful-Booker (Bookings)

**Base URL:** `https://restful-booker.herokuapp.com`

---

### API_BOOK_001 — Create auth token

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/auth` |
| **Priority** | High |

**Request Body:**
```json
{
  "username": "admin",
  "password": "password123"
}
```

**Expected Response:**
- Status code: `200 OK`
- Response contains a `token` field used for authenticated requests

---

### API_BOOK_002 — Get all booking IDs

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/booking` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `200 OK`
- Body is a JSON array of objects each containing `bookingid`

---

### API_BOOK_003 — Create a new booking

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/booking` |
| **Priority** | High |

**Request Body:**
```json
{
  "firstname": "John",
  "lastname": "Tester",
  "totalprice": 150,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2026-01-01",
    "checkout": "2026-01-05"
  },
  "additionalneeds": "Breakfast"
}
```

**Expected Response:**
- Status code: `200 OK`
- Response contains `bookingid` and a `booking` object matching the sent data

---

### API_BOOK_004 — Get a booking by ID

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/booking/{id}` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `200 OK`
- Response contains the full booking details for that ID

---

### API_BOOK_005 — Update a booking (requires token)

| Field | Value |
|---|---|
| **Method** | PUT |
| **Endpoint** | `/booking/{id}` |
| **Priority** | High |
| **Headers** | `Content-Type: application/json`, `Cookie: token={token}` |

**Request Body:**
```json
{
  "firstname": "Jane",
  "lastname": "Updated",
  "totalprice": 200,
  "depositpaid": false,
  "bookingdates": {
    "checkin": "2026-02-01",
    "checkout": "2026-02-10"
  },
  "additionalneeds": "Late checkout"
}
```

**Expected Response:**
- Status code: `200 OK`
- Response reflects the updated booking values

---

### API_BOOK_006 — Update without auth token (negative)

| Field | Value |
|---|---|
| **Method** | PUT |
| **Endpoint** | `/booking/{id}` |
| **Priority** | High |

**Steps:** Send a PUT request without the `Cookie: token` header.

**Expected Response:**
- Status code: `403 Forbidden`
- Update is rejected

---

### API_BOOK_007 — Delete a booking

| Field | Value |
|---|---|
| **Method** | DELETE |
| **Endpoint** | `/booking/{id}` |
| **Priority** | Medium |
| **Headers** | `Cookie: token={token}` |

**Expected Response:**
- Status code: `201 Created`
- Booking is removed; a subsequent GET returns `404 Not Found`
