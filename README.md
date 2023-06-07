
# Microservices RESTful API for restaurant

## Target
Develop two RESTful API-based microservices for a restaurant order processing system, the first of which implements user authorization with different roles, and the second manages orders and tracks the stock of dishes.


## API Reference
### Authorization microservice

#### [ALL] Registration
```
POST /register
```
##### Body
```
{
    "username":"kolpakovee",
    "email":"kolpakovee@bk.ru",
    "password":"12345",
    "role":"MANAGER"
}
```

#### [ALL] Authorization
```
POST /login
```
##### Body
```
{
    "email":"kolpakovee@bk.ru",
    "password":"12345"
}
```

#### [AUTH] Validation 
```
GET /validate
```
##### Authorization
```
Bearer {your JWT token}
```

#### [AUTH] Get info about user
```
GET /user-info
```
##### Authorization
```
Bearer {your JWT token}
```

### Restaurant microservice
#### [AUTH] Get menu
```
GET /menu
```
##### Authorization
```
Bearer {your JWT token}
```

#### [MANAGER] Get dish by id
```
GET /restaurant/dsih/{id}
```
##### Authorization
```
Bearer {your JWT token}
```

#### [MANAGER] Create new dish
```
POST /restaurant/dish/create
```
##### Authorization
```
Bearer {your JWT token}
```
##### Body
```
{
   "name":"Chicken steak",
   "description":"Very soft and tender meat",
   "price":400,
   "quantity":10,
   "available":true
}
```

#### [MANAGER] Update dish by id
```
PUT /restaurant/dish/{id}
```
##### Authorization
```
Bearer {your JWT token}
```
##### Body
```
{
   "name":"Chicken steak",
   "description":"Very soft and tender meat",
   "price":350,
   "quantity":10,
   "available":true
}
```

#### [MANAGER] Delete dish by id
```
DELETE /restaurant/dish/{id}
```
##### Authorization
```
Bearer {your JWT token}
```

#### [AUTH] Create new order
```
POST /restaurant/order/create
```
##### Authorization
```
Bearer {your JWT token}
```
##### Body
```
{
   "specialRequests":"Very fast, please",
   "orderDishList":[
      {
         "dishId":6,
         "quantity":2,
         "price":500
      },
      {
         "dishId":7,
         "quantity":3,
         "price":400
      }
   ]
}
```

#### [AUTH] Get order by id
```
GET /restaurant/order/{id}
```
##### Authorization
```
Bearer {your JWT token}
```

## Tech Stack

**auth-service:** Java, Spring (Web, Data JPA, PostgreSQL Driver, Security, Validation, Lombok), Maven, PostgreSQL, JJWT

**restaurant-service:** Java, Spring (Web, Data JPA, PostgreSQL Driver, Validation, Lombok), Maven, PostgreSQL

**api-gateway**: Java, Spring(Web, Gateway, WebFlux, Lombok), Maven



