{
  "info": {
    "name": "JSONPlaceholder API Tests",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "variable": [
    {
      "key": "baseUrl",
      "value": "https://jsonplaceholder.typicode.com"
    }
  ],
  "item": [
    {
      "name": "GET all posts",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts"
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "pm.test(\"Response time < 2000 ms\", () => pm.expect(pm.response.responseTime).to.be.below(2000));",
              "const j = pm.response.json();",
              "pm.test(\"Returns array of 100 posts\", () => { pm.expect(j).to.be.an(\"array\"); pm.expect(j.length).to.eql(100); });"
            ]
          }
        }
      ]
    },
    {
      "name": "GET single post",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts/1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts",
            "1"
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "const j = pm.response.json();",
              "pm.test(\"Has expected fields\", () => { pm.expect(j).to.have.all.keys(\"userId\",\"id\",\"title\",\"body\"); pm.expect(j.id).to.eql(1); });"
            ]
          }
        }
      ]
    },
    {
      "name": "GET posts filtered by userId",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts?userId=1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts"
          ],
          "query": [
            {
              "key": "userId",
              "value": "1"
            }
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "const j = pm.response.json();",
              "pm.test(\"All posts belong to userId 1\", () => j.forEach(p => pm.expect(p.userId).to.eql(1)));"
            ]
          }
        }
      ]
    },
    {
      "name": "GET non-existent post (negative)",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts/9999",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts",
            "9999"
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 404\", () => pm.response.to.have.status(404));"
            ]
          }
        }
      ]
    },
    {
      "name": "GET user schema",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/users/1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "users",
            "1"
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "const u = pm.response.json();",
              "pm.test(\"User schema\", () => { pm.expect(u.name).to.be.a(\"string\"); pm.expect(u.email).to.include(\"@\"); pm.expect(u.address).to.be.an(\"object\"); });"
            ]
          }
        }
      ]
    },
    {
      "name": "GET comments for post",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/comments?postId=1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "comments"
          ],
          "query": [
            {
              "key": "postId",
              "value": "1"
            }
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "pm.test(\"Comments returned\", () => pm.expect(pm.response.json().length).to.be.above(0));"
            ]
          }
        }
      ]
    },
    {
      "name": "POST create post",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts"
          ]
        },
        "body": {
          "mode": "raw",
          "raw": "{\n  \"title\": \"QA test post\",\n  \"body\": \"created via Postman\",\n  \"userId\": 1\n}"
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 201\", () => pm.response.to.have.status(201));",
              "const j = pm.response.json();",
              "pm.test(\"Echoes request data and returns id\", () => { pm.expect(j.title).to.eql(\"QA test post\"); pm.expect(j.id).to.exist; });"
            ]
          }
        }
      ]
    },
    {
      "name": "PUT update post",
      "request": {
        "method": "PUT",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts/1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts",
            "1"
          ]
        },
        "body": {
          "mode": "raw",
          "raw": "{\n  \"id\": 1,\n  \"title\": \"updated title\",\n  \"body\": \"updated body\",\n  \"userId\": 1\n}"
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));",
              "pm.test(\"Title updated\", () => pm.expect(pm.response.json().title).to.eql(\"updated title\"));"
            ]
          }
        }
      ]
    },
    {
      "name": "DELETE post",
      "request": {
        "method": "DELETE",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": {
          "raw": "{{baseUrl}}/posts/1",
          "host": [
            "{{baseUrl}}"
          ],
          "path": [
            "posts",
            "1"
          ]
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "type": "text/javascript",
            "exec": [
              "pm.test(\"Status code is 200\", () => pm.response.to.have.status(200));"
            ]
          }
        }
      ]
    }
  ]
}