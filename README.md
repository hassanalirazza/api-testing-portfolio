# API Testing Portfolio

A collection of REST API test cases and documentation demonstrating API validation — status codes, response payloads, data integrity, and error handling.

All examples use **free, public APIs** — no proprietary or confidential data.

---

## Public APIs Used

| API | Purpose |
|---|---|
| [JSONPlaceholder](https://jsonplaceholder.typicode.com) | CRUD operations on posts/resources |
| [ReqRes](https://reqres.in) | Authentication, registration, user data |
| [Restful-Booker](https://restful-booker.herokuapp.com) | Booking creation, auth tokens, updates |

---

## What's Inside

| Folder | Contents |
|---|---|
| [`api-test-cases/`](./api-test-cases) | Detailed API test cases per endpoint |
| [`postman/`](./postman) | How the Postman collection is structured and how to run it |
| [`reference/`](./reference) | HTTP status code quick reference for testers |

---

## What These Test Cases Cover

- **HTTP methods:** GET, POST, PUT, PATCH, DELETE
- **Status code validation:** 200, 201, 400, 401, 404, etc.
- **Response body validation:** field presence, data types, values
- **Authentication:** token generation and protected endpoints
- **Negative testing:** invalid payloads, missing fields, unauthorized access

---

## Testing Approach

Each API test case documents the request (method, endpoint, headers, body), the expected response (status code + body), and the validation checks a tester performs. This mirrors how API testing is structured in tools like Postman.

---

## About Me

QA Engineer with 5 years of experience, including REST API validation using Postman across web, mobile, and cloud applications.
Profile: [github.com/hassanalirazza](https://github.com/hassanalirazza)
