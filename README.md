#Learning API
Description
This repository contains a Postman collection for testing the "Learning" API. Below, you will find a description of available endpoints along with sample requests and tests.

Requests
1. Get all posts
Endpoint: GET /posts

Tests:

javascript
Copy code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
2. Get the first post
Endpoint: GET /posts/1

Tests:

javascript
Copy code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
3. Filters
Endpoint: GET /posts?title=json-server&author=typicode

Tests:

javascript
Copy code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
4. Add a new post
Endpoint: POST /posts

Tests:

javascript
Copy code
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

pm.test("Check title", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.title).to.eql(pm.globals.get("title"));
});

pm.test("Check author", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.author).to.eql(pm.environment.get("randomName"));
});
Pre-request:

javascript
Copy code
pm.environment.set("randomName", pm.variables.replaceIn('{{$randomFullName}}'));
5. Update a post
Endpoint: PUT /posts/1

Tests:

javascript
Copy code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
6. Update one part of a post
Endpoint: PATCH /posts/5

Tests:

javascript
Copy code
pm.test("Status code is 404", function () {
    pm.response.to.have.status(404);
});
7. Add a new post to delete
Endpoint: POST /posts

Tests:

javascript
Copy code
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

pm.test("Check title", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.title).to.eql(pm.globals.get("title"));
});

pm.test("Check author", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.author).to.eql(pm.environment.get("randomName"));
});

pm.globals.set("postidtodelete", pm.response.json().id);
Pre-request:

javascript
Copy code
pm.environment.set("randomName", pm.variables.replaceIn('{{$randomFullName}}'));
8. Delete a post
Endpoint: DELETE /posts/{{postidtodelete}}

Tests:

javascript
Copy code
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
Access the API server at: http://{{host}}:3000
