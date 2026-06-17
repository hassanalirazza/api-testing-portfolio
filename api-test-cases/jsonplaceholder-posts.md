# API Test Cases — JSONPlaceholder (Posts)

**Base URL:** `https://jsonplaceholder.typicode.com`
**Resource:** `/posts`

---

### API_POST_001 — Get all posts

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/posts` |
| **Priority** | High |

**Expected Response:**
- Status code: `200 OK`
- Body is a JSON array
- Array contains 100 post objects
- Each object has `userId`, `id`, `title`, `body`

---

### API_POST_002 — Get a single post by ID

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/posts/1` |
| **Priority** | High |

**Expected Response:**
- Status code: `200 OK`
- Body is a single JSON object
- `id` equals `1`
- `title` and `body` are non-empty strings

---

### API_POST_003 — Get a non-existent post

| Field | Value |
|---|---|
| **Method** | GET |
| **Endpoint** | `/posts/9999` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `404 Not Found`
- Body is an empty object

---

### API_POST_004 — Create a new post

| Field | Value |
|---|---|
| **Method** | POST |
| **Endpoint** | `/posts` |
| **Priority** | High |

**Request Body:**
```json
{
  "title": "QA Test Post",
  "body": "Testing post creation",
  "userId": 1
}
```

**Expected Response:**
- Status code: `201 Created`
- Response echoes the sent fields
- A new `id` is returned

---

### API_POST_005 — Update an existing post (PUT)

| Field | Value |
|---|---|
| **Method** | PUT |
| **Endpoint** | `/posts/1` |
| **Priority** | Medium |

**Request Body:**
```json
{
  "title": "Updated Title",
  "body": "Updated body content",
  "userId": 1
}
```

**Expected Response:**
- Status code: `200 OK`
- Response reflects the updated values
- `id` remains `1`

---

### API_POST_006 — Delete a post

| Field | Value |
|---|---|
| **Method** | DELETE |
| **Endpoint** | `/posts/1` |
| **Priority** | Medium |

**Expected Response:**
- Status code: `200 OK`
- Post is treated as deleted (empty object returned)
