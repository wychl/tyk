## user list 
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/users | python -mjson.tool
```

## get user 

```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/users/59eee1198f3cf5a56213d740 | python -mjson.tool
```

## add user
```bash
curl -X POST -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
     -s \
     -H "Content-Type: application/json" \
     -X POST \
     -d '{
                "first_name": "test",
               "last_name": "test",
               "email_address": "test@jasonsonson.com",
               "active": true,
               "password": "test123456"
     }' http://localhost:3000/api/users | python -mjson.tool
```