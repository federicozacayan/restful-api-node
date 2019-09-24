# RESTful API web server dockerized on Node

This is a basic Hello-Wolrd appplication.

## Requirements

It is assumed you have Linux OS, but you can run this project in Windows or MacOS also, just use the alternative  lines commands.

**Linux**

- `Docker` installed
- `docker-compose` installed
- Any rest consumer application like `Postman` installed or any plugin REST client in any browser (like "Advanced REST client" in Chrome )

## Set up

Running in linux console.

### Prepare

Clone this repository.

```bash
git clone https://github.com/federicozacayan/restful-api-node.git node-tutorial
```

### Run

Run the following command in the  the root folder.

```bash
sudo docker-compose up
```

### Stop

Press `CTRL+C` on the console.

### Clean your disk

Run the following command to remove the container first and his image after.

```bash
sudo docker rm node mongo && sudo docker rmi node_with_dependencies:1.0 mongo
```

## Tutorial

You can find a tutorial of this project in the following site.

[https://federicozacayan.github.io/tutorial/restful-api-node/](https://federicozacayan.github.io/tutorial/restful-api-node/)

## Usage

All the responses have `ContentType application/json` header.

### List all products

**Definition**

`GET /products`

**Response**

- `200 OK` on success.

```json
{
    "count": 3,
    "products": [
        {
            "name": "Federico Zacayan",
            "price": 10,
            "_id": "5d8a0988c56114001d6544bd",
            "request": {
                "type": "GET",
                "url": "http://localhost:3000/products/5d8a0988c56114001d6544bd"
            }
        },
        {
            "name": "Software Developer",
            "price": 10,
            "_id": "5d8a098ec56114001d6544be",
            "request": {
                "type": "GET",
                "url": "http://localhost:3000/products/5d8a098ec56114001d6544be"
            }
        }
    ]
}
```

### Registering a new product

**Definition**

`POST /products`

**Arguments**

- `"name":string` a friendly name for this product.
- `"name":number` a friendly name for this product.

**Response**

- `201 Created` on success.

```json
{
    "message": "Created product successfully",
    "createdProduct": {
        "name": "Federico Zacayan",
        "price": 10,
        "_id": "5d8a098ec56114001d6544be",
        "request": {
            "type": "GET",
            "url": "http://localhost:3000/products/5d8a098ec56114001d6544be"
        }
    }
}
```

## Lookup product details

`GET /products/<identifier>`

**Response**

- `200 OK` on success.

```json
{
    "product": {
        "_id": "5d8a0988c56114001d6544bd",
        "name": "Federico Zacayanr",
        "price": 10
    },
    "request": {
        "type": "GET",
        "url": "http://localhost:3000/products"
    }
}
```
## update products

`PATCH /products/<identifier>`
**Arguments**

- `array` with objects which represents the fields.
  - `propName:string` name of property
  - `value:Mixed` value of property
```json
[
	{
		"propName":"name",
		"value":"Federico Zacayaan"
	}
]
```

**Response**

- `200 OK` on success.

```json
{
    "product": {
        "_id": "5d8a0988c56114001d6544bd",
        "name": "Federico Zacayanr",
        "price": 10
    },
    "request": {
        "type": "GET",
        "url": "http://localhost:3000/products"
    }
}
```

## Delete a product

**Definition**

`DELETE /products/<identifier>`

**Response**

- `500 Internal Error` if the product does not exist.
- `200 No Content` on success.
```json
{
    "message": "Product deleted",
    "request": {
        "type": "POST",
        "url": "http://localhost:3000/products",
        "body": {
            "name": "String",
            "price": "Number"
        }
    }
}
