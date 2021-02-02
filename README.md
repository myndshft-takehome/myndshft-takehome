
# TODO

Todo is a simple little app. It allows a user to enter, update, and delete items they 
need to complete and keep track of their completion status.

## Setup

To get started, you will want to review the backend API we have setup for you to use.
See the Docs section for the breakdown of the API calls and DB models. 

You will submit all your API calls to the appropriate endpoint on the same site 
(/docs is for documentation, /items is for the todos, etc.).

Please note that the database is empty upon starting, which means that you'll have to use
the POST route in order to populate the array received in the GET route for items. 

Your job is to get a nice UI around this API completed so users can manage their todo
lists more effectively. Remember to commit and push as often as possible, 
WE'D MUCH RATHER SEE AN INCOMPLETE RESPONSE THAN NOTHING AT ALL. Wherever you get 
to in the time limit, commit and push it.

If you have any questions, issues with the API, or need clarification, please feel
free to reach out to either Tyler (tyler@myndshft.com) or Kyle (kyle@myndshft.com).

Good luck and we look forward to seeing your submission!

## Docs

### APIs / Paths

```
"info": {
  "title": "Myndshft Take Home Test",
  "name": "git.takehome.io",
  "version": "1.0.0"
},
"paths": {
  "/": {
    "get": {
      "responses": {
        "200": {
          "description": "Successful Response",
          "content": {
            "application/json": {
              "schema": {

              }
            }
          }
        }
      },
      "summary": "Read Root",
      "operationId": "read_root__get"
    }
  },
  "/items/{item_id}": {
    "get": {
      "responses": {
        "200": {
          "description": "Successful Response",
          "content": {
            "application/json": {
              "schema": {

              }
            }
          }
        },
        "422": {
          "description": "Validation Error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HTTPValidationError"
              }
            }
          }
        }
      },
      "summary": "Read Item",
      "operationId": "read_item_items__item_id__get",
      "parameters": [
        {
          "required": true,
          "schema": {
            "title": "Item_Id",
            "type": "string"
          },
          "name": "item_id",
          "in": "path"
        },
        {
          "description": "The UUID given to you in the instructions",
          "required": true,
          "schema": {
            "title": "Candidate-Uuid",
            "type": "string",
            "description": "The UUID given to you in the instructions"
          },
          "name": "candidate-uuid",
          "in": "header"
        }
      ]
    },
    "put": {
      "responses": {
        "200": {
          "description": "Id of the modified Item",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Item"
              }
            }
          }
        },
        "422": {
          "description": "Validation Error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HTTPValidationError"
              }
            }
          }
        }
      },
      "summary": "Update Item",
      "operationId": "update_item_items__item_id__put",
      "parameters": [
        {
          "required": true,
          "schema": {
            "title": "Item_Id",
            "type": "string"
          },
          "name": "item_id",
          "in": "path"
        },
        {
          "description": "The UUID given to you in the instructions",
          "required": true,
          "schema": {
            "title": "Candidate-Uuid",
            "type": "string",
            "description": "The UUID given to you in the instructions"
          },
          "name": "candidate-uuid",
          "in": "header"
        }
      ],
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/ItemIn"
            }
          }
        },
        "required": true
      }
    },
    "delete": {
      "responses": {
        "204": {
          "description": "Successful Response",
          "content": {
            "application/json": {
              "schema": {

              }
            }
          }
        },
        "422": {
          "description": "Validation Error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HTTPValidationError"
              }
            }
          }
        }
      },
      "summary": "Delete Item",
      "operationId": "delete_item_items__item_id__delete",
      "parameters": [
        {
          "required": true,
          "schema": {
            "title": "Item_Id",
            "type": "string"
          },
          "name": "item_id",
          "in": "path"
        },
        {
          "description": "The UUID given to you in the instructions",
          "required": true,
          "schema": {
            "title": "Candidate-Uuid",
            "type": "string",
            "description": "The UUID given to you in the instructions"
          },
          "name": "candidate-uuid",
          "in": "header"
        }
      ]
    }
  },
  "/items/": {
    "get": {
      "responses": {
        "200": {
          "description": "Successful Response",
          "content": {
            "application/json": {
              "schema": {
                "title": "Response_Read_Items",
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/Item"
                }
              }
            }
          }
        },
        "422": {
          "description": "Validation Error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HTTPValidationError"
              }
            }
          }
        }
      },
      "summary": "Read Items",
      "operationId": "read_items_items__get",
      "parameters": [
        {
          "required": false,
          "schema": {
            "title": "Title",
            "type": "string"
          },
          "name": "title",
          "in": "query"
        },
        {
          "required": false,
          "schema": {
            "title": "Description",
            "type": "string"
          },
          "name": "description",
          "in": "query"
        },
        {
          "required": false,
          "schema": {
            "title": "Done",
            "type": "boolean"
          },
          "name": "done",
          "in": "query"
        },
        {
          "description": "The UUID given to you in the instructions",
          "required": true,
          "schema": {
            "title": "Candidate-Uuid",
            "type": "string",
            "description": "The UUID given to you in the instructions"
          },
          "name": "candidate-uuid",
          "in": "header"
        }
      ]
    }
  },
  "/items": {
    "post": {
      "responses": {
        "200": {
          "description": "Successful Response",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Item"
              }
            }
          }
        },
        "422": {
          "description": "Validation Error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/HTTPValidationError"
              }
            }
          }
        }
      },
      "summary": "Create Item",
      "operationId": "create_item_items_post",
      "parameters": [
        {
          "description": "The UUID given to you in the instructions",
          "required": true,
          "schema": {
            "title": "Candidate-Uuid",
            "type": "string",
            "description": "The UUID given to you in the instructions"
          },
          "name": "candidate-uuid",
          "in": "header"
        }
      ],
      "requestBody": {
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/ItemIn"
            }
          }
        },
        "required": true
      }
    }
  }
}
```
### Models / Schemas

```
"ItemIn": {
  "title": "ItemIn",
  "required": [
    "title",
    "description"
  ],
  "type": "object",
  "properties": {
    "title": {
      "title": "Title",
      "type": "string"
    },
    "description": {
      "title": "Description",
      "type": "string"
    },
    "done": {
      "title": "Done",
      "type": "boolean",
      "default": false
    }
  }
},
"Item": {
  "title": "Item",
  "required": [
    "id",
    "title",
    "description",
    "created"
  ],
  "type": "object",
  "properties": {
    "id": {
      "title": "Id",
      "type": "string"
    },
    "title": {
      "title": "Title",
      "type": "string"
    },
    "description": {
      "title": "Description",
      "type": "string"
    },
    "created": {
      "title": "Created",
      "type": "string",
      "format": "date-time"
    },
    "done": {
      "title": "Done",
      "type": "boolean",
      "default": false
    }
  }
},
"ValidationError": {
  "title": "ValidationError",
  "required": [
    "loc",
    "msg",
    "type"
  ],
  "type": "object",
  "properties": {
    "loc": {
      "title": "Location",
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "msg": {
      "title": "Message",
      "type": "string"
    },
    "type": {
      "title": "Error Type",
      "type": "string"
    }
  }
},
"HTTPValidationError": {
  "title": "HTTPValidationError",
  "type": "object",
  "properties": {
    "detail": {
      "title": "Detail",
      "type": "array",
      "items": {
        "$ref": "#/components/schemas/ValidationError"
      }
    }
  }
}
```


