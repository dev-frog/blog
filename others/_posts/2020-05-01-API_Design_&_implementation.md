---
layout: post
title: REST API Design and Implementation 
description: >

---

# REST API Design and Implementation 

## 1. Characteristics of an effective API design

- Easy to use and work with.
- Hard to misuse.
- Complete and concise.
- Easy to read and maintain code that uses it.

### 1.1 naming

- Use nouns to represent resources.
  - `/store/customers/{id}`
- Leverage logical grouping and reflection object relationships.
  -`/customers/{customerId}/accounts/{accountId}/transactions/{transactionId}`
- Use plural nouns to represent collections.
- Collection is a group of resources.
- Use hyphens to improve readability.

### 1.2. Use HATEOAS (Hypermedia as the Engine of Application State) to enable navigation to resources.

- Constraint of the REST application architecture that keeps the RESTful style architecture unique from most other network application architectures.
- Component of the media type that you select for your API and enables you to navigate to the resources of the API.
- It is a way to navigate to resources that are related to the current resource.

### 1.3. Provide filtering, sorting, field selection and paging for collections.

- To filter data by specific key-value pairs, use query parameters.
  - `/customers?state=CA`
- To fetch only specific fields by key
  - `/customers?fields=name,age`
- To limit the number of items for the data returned, use the `limit` query parameter.
  - `/customers?limit=10`
- To skip a number of items, use the `offset` query parameter.
    - `/customers?offset=10`
- To pagonate the data chunk by chunk instead of querying all at once.
    - `/customers?offset=10&limit=10`
- To sort the data by a specific key-value.
    - `/customers?sort=name`
    - `/customers?sort=-name` (descending order)
- Route controller should not rely on side-effects.
- Same request repeated for the same resource should return the same response in the same state.
- Use the appropriate HTTP verbs to make it easy to use.
  - `GET` - Retrieve a resource.
  - `POST` - Create a resource.
  - `PUT` - Update a resource.
  - `PATCH` - Partially update a resource.
  - `DELETE` - Delete a resource.
- Use HTTP status codes to return the appropriate status.
    - `200` - OK
    - `201` - Created
    - `204` - No Content
    - `400` - Bad Request
    - `401` - Unauthorized
    - `403` - Forbidden
    - `404` - Not Found
    - `405` - Method Not Allowed
    - `500` - Internal Server Error
- Use HTTP headers for serialization formats.
  - `Accept` - Request header that specifies the response format.
  - `Content-Type` - Entity header that specifies the request format.

### 1.4. Handle Errors with HTTP status codes.

- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `405` - Method Not Allowed
- `500` - Internal Server Error

### 1.5. Partial Responses

- In order to improve the speed of loading those assets users should be able to review them in chunks.

### 1.6. Error Handling

- Endpoint users need to know that went wrong to be able to fix the request.
- But also make sure you don't expose the internal mechanism of your controller.
- Make sure you return the correct HTTP status code, there are a lot of them.

### 1.7. Security

- Make SSL/TLS encryption a default for your API endpoints.
- Authorization should be handled using the `Authorization` header and providing a token.
- Implement ACLs (Access Control Lists) to restrict access to certain resources.
- Rate limit API calls to prevent DDoS attacks.

### 1.8. Documentation

- Make sure you document your API endpoints.
- Make sure you document the request and response formats.
- Make sure you document the errors that can be returned.
