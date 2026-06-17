# Postman Collection Guide

This folder documents how the API test cases in this repository are organized and executed in Postman.

---

## Collection Structure

A Postman collection for this portfolio would be organized into folders per API:

```
API Testing Portfolio (Collection)
├── JSONPlaceholder
│   ├── GET all posts
│   ├── GET single post
│   ├── POST create post
│   ├── PUT update post
│   └── DELETE post
├── ReqRes
│   ├── POST login
│   ├── POST register
│   └── GET user
└── Restful-Booker
    ├── POST auth (get token)
    ├── POST create booking
    ├── GET booking
    ├── PUT update booking
    └── DELETE booking
```

---

## How API Tests Are Validated in Postman

Each request includes assertions written in the **Tests** tab to validate the response automatically.

**Example — validate status code and response body:**

```javascript
// Status code check
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// Response field check
pm.test("Response has a token", function () {
    const json = pm.response.json();
    pm.expect(json).to.have.property("token");
    pm.expect(json.token).to.be.a("string");
});
```

---

## Using Variables for Auth Tokens

For APIs that require authentication (e.g., Restful-Booker), the token from the auth request is saved to a collection variable and reused in later requests.

**In the auth request's Tests tab:**

```javascript
pm.test("Token generated", function () {
    const json = pm.response.json();
    pm.expect(json).to.have.property("token");
    pm.collectionVariables.set("authToken", json.token);
});
```

**In subsequent requests**, the token is referenced as `{{authToken}}` in the headers.

---

## Running the Whole Collection

The full collection can be executed at once using the **Postman Collection Runner**, which runs every request in sequence and reports pass/fail results for all assertions — useful for regression checks against an API.

---

## Note

This guide documents the testing approach using public APIs. No proprietary collections or company endpoints are included.
