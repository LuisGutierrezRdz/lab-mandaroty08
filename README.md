# lab-mandaroty08

## API Design Session:
* **Endpoint Design:**
  * Participants will define RESTful API endpoints for user management, order processing, and customer service interactions.
* **Resource Modeling:**
  * Define the data structures and resource models required to support the API functionality, such as user profiles, order details, and customer tickets.
* **Documentation:**
  * Document each API endpoint, specifying required parameters, possible responses, and error codes to ensure clarity and completeness. Emphasis will be placed on adherence to best practices in API documentation to enhance ease of use and maintainability.
 
## Solution
```
  openapi: 3.0.0
info:
  version: 1.0.0
  title: e-commerce system
  description: e-commerce system
  contact:
    name: José Luis Gutiérrez Rodríguez
    email: jose.gutierrez@spinbyoxxo.com.mx
servers:
  - description: Dev Server
    url: https://ecommerce.com/
paths: {
  "/v1/users": {
    "post" : {
      "tags": ["users"],
      "summary": "Create user",
      "description" : "Create users",
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/user"
            }
          }
        }
      },
      "responses" : {
        "201" : {
          "description" : "Created",
          "content" : {
            "application/json": {
              "schema" : {
                "type" : "array",
                "items" : {
                  "$ref": "#/components/schemas/user"
                }
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    }
  },
  "/v1/users/{id}": {
    "get" : {
      "tags": ["users"],
      "summary": "Get user",
      "description" : "Get user",
      "parameters":[
        {
          "name": "id",
          "in": "path",
          "required": true,
          "schema": { "type": "string", "example": "1231243123" }
        }
      ],
      "responses" : {
        "200" : {
          "description" : "Success",
          "content" : {
            "application/json": {
              "schema" : {
                "type" : "array",
                "items" : {
                  "$ref": "#/components/schemas/user"
                }
              }
            }
          }
        },
        "404" : {
          "description" : "Not found",
          "content" : {
            "application/json": {
              "schema" : {
                "type" : "string"
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    },
    "put" : {
      "tags": ["users"],
      "summary": "Update user",
      "description" : "Update user",
      "parameters":[
        {
          "name": "id",
          "in": "path",
          "required": true,
          "schema": { "type": "string", "example": "1231243123" }
        }
      ],
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/update-user"
            }
          }
        }
      },
      "responses" : {
        "201" : {
          "description" : "Created",
          "content" : {
            "application/json": {
              "schema" : {
                "type" : "array",
                "items" : {
                  "$ref": "#/components/schemas/user"
                }
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    },
    "delete" : {
      "tags": ["users"],
      "summary": "Delete user",
      "description" : "Delete user",
      "parameters":[
        {
          "name": "id",
          "in": "path",
          "required": true,
          "schema": { "type": "string", "example": "1231243123" }
        }
      ],
      "responses" : {
        "204" : {
          "description" : "No content"
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    }
  },
  "/v1/orders": {
    "post": {
      "tags": [ "orders" ],
      "summary": "Create order",
      "description": "Create order",
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/order"
            }
          }
        }
      },
      "responses": {
        "201": {
          "description": "Created",
          "content": {
            "application/json": {
              "schema": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/orderResponse"
                }
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    }
  },
  "/v1/orders/{orderId}": {
    "get": {
      "tags": [ "orders" ],
      "summary": "Get order by id",
      "description": "Get order by id",
      "parameters":[
        {
          "name": "orderId",
          "in": "path",
          "required": true,
          "schema": { "type": "integer", "example": "123123" }
        }
      ],
      "responses": {
        "200": {
          "description": "Success",
          "content": {
            "application/json": {
              "schema": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/orderResponse"
                }
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    },
    "put": {
      "tags": [ "orders" ],
      "summary": "Update order",
      "description": "Update order",
      "parameters":[
        {
          "name": "orderId",
          "in": "path",
          "required": true,
          "schema": { "type": "integer", "example": "123123" }
        }
      ],
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/order"
            }
          }
        }
      },
      "responses": {
        "200": {
          "description": "Created",
          "content": {
            "application/json": {
              "schema": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/orderResponse"
                }
              }
            }
          }
        },
        "400":{
          "description": "Invalid request"
        },
        "500": {
          "description": "Internal server error"
        }
      }
    }
  }
}
components:
  schemas:
    user:
      type: object
      properties:
        id:
          type: integer
          format: int32
          example: 123123123001
        email:
          type: string
          nullable: true
        nicke-name:
          type: string
          nullable: true
        profile :
          nullable: false
          enum: [PREMIUM, ADMIN, NORMAL]
          example: "PREMIUM"
        createdAt:
          type: string
          format: date-time
        updatedAt:
          type: string
          format: date-time
    update-user:
      type: object
      properties:
        email:
          type: string
          nullable: true
        nicke-name:
          type: string
          nullable: true
        profile :
          nullable: false
          enum: [PREMIUM, ADMIN, NORMAL]
          example: "NORMAL"
    order:
      type: object
      properties:
        orderNumber:
          type: string
          nullable: false
        products:
          type: array
          items: {"$ref": "#/components/schemas/product"}
    orderResponse:
      type: object
      properties:
        orderNumber:
          type: string
          nullable: false
        createdAt:
          type: string
          format: date
          nullable: false
        userId:
          type: string
          nullable: false
        products:
          type: array
          items: { "$ref": "#/components/schemas/product" }
    product:
      type: object
      properties:
        id:
          type: integer
          format: int32
          example: 123123123001
        name:
          type: string
          nullable: false
        price:
          type: number
          nullable: false
```

![image](https://github.com/LuisGutierrezRdz/lab-mandaroty08/assets/115661340/fe95a521-6dce-4c73-953c-e4fc7f46de78)
![image](https://github.com/LuisGutierrezRdz/lab-mandaroty08/assets/115661340/1f29c821-db93-47eb-bcf3-ead8579100c7)
![image](https://github.com/LuisGutierrezRdz/lab-mandaroty08/assets/115661340/3584365f-36b8-4b59-a6f9-9cd6a106dc48)


