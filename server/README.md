docs: https://graphql.org/learn/queries/
https://graphql.org/graphql-js/mutations-and-input-types/
run data server: npx json-server --watch data.json
run express server: node server.js
check if its running: curl http://localhost:3000/products/1
to watch the data with graphicQL: open http://localhost:4000/graphql on browser

query one product:
example 1:
{
  product(id:"1") {
    name
  }
}

example 2:
{
  product(id:"1") {
    id,
    name,
    category,
    price
  }
}

query all products:
example 1:
{
  products {
    id,
    name,
    price,
    category
  }
}

example 2:
{
  products {
		category
  }
}

example 3:
{
  users {
    id,
    name,
    email,
    password,
    role
  }
}

example 4:
{
  users {
    id,
    name,
    email,
    password,
    role,
    createdProducts {
      id,
      name,
      category,
      price
    }
  }
}

mutation addProduct:
mutation{
  addProduct(name: "Computer", category: "Technology", price: 200) {
    id,
    name,
    category,
    price
  }
}

mutation deleteProduct (note: change id of id generated by addProductmutation):
mutation{
  deleteProduct(id:"ML2lVSj"){
    id
  }
}

mutation editProduct:
mutation{
	editProduct(id:"1", price: 15){
  	id,
  	name,
  	category,
  	price  
	}
}

PRISMA CRUD OPERATIONS:

create:
curl -s -X POST -H 'content-type: application/json' -d '{"name": "User from Curl Request", "email": "user@curl.com", "password": "12345", "role": "admin" }' localhost:4000/users | json

curl -s -X POST -H 'content-type: application/json' -d '{"createdBy": 2 }' localhost:4000/shoppingCarts | json
 
curl -s -X POST -H 'content-type: application/json' -d '{"name": "Ball", "category": "Sports", "price": 30 }' localhost:4000/products | json

read:
curl -s localhost:4000/products | json
curl -s localhost:4000/shoppingCarts | json

delete:
curl -s -X DELETE localhost:4000/products/4 | json
curl -s -X DELETE localhost:4000/shoppingCarts/3 | json

after prisma updates on models:
// pushear cambios de models
$ npx prisma db push
// para actualizar el cliente de prisma
$ npx prisma generate
// después de actualizar el cliente, volver a arrancar prisma studio (refresh)



docker comands:

check docker images:
docker ps -a

run (start) docker image:
docker start docker-image-name
in this case: docker start e-commerce-postgresql

check running (started) docker images:
docker ps

