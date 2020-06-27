## Building a simple task queue in node.js with bee-queue and redis.
>Check out the link to read the published article

### To run it locally

```sh
$ npm install
$ npm start
```
#### Endpoints
+ GET `/`

Check restaurant status

+ POST `/order` with `JSON` body

> Request body
```json
{
  "dish": "Chicken Al-faham",
  "qty": 2
}
```

> Response body
```json
{
  "done": true,
  "order": "22",
  "message": "Your order will be ready in a while"
}
```

+ GET `/status` with query strings

> Request query
```js
{
  orderId: 22
}
```
> Example

`http://localhost:5000/status?orderId=22`

> Response body
When the job is running:
```json
{
  "progress": "Your order is ⏲ 32.5% ready",
  "order": {
    "dish": "Pork ribs",
    "qty": 8
  },
  "status": "created"
}
```
When the job is finished:
```json
{
  "progress": "Your order is ready 😊",
  "order": {
    "dish": "Pork ribs",
    "qty": 8
  }
}
```

+ POST `/order-legacy` with `JSON` body

> Request body
```json
{
  "dish": "Tacos",
  "qty": 4
}
```

> Response body
```json
{
  "done": true,
  "message": "Your 4x Tacos is ready"
}
```

