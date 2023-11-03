## Get all fields for given key in redis cache
Maybe turn it into CMD line tool.
```
import redis # pip install redis
HOST = "HOST" # Replace with host
PORT = 6379
r = redis.Redis(host=HOST, port=PORT, decode_responses=False)
r.hgetall(b'<KEY>')[b'<FIELD>']
```

