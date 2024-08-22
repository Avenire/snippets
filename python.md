## Get all fields for given key in redis cache
Maybe turn it into CMD line tool.
```
import redis # pip install redis
HOST = "HOST" # Replace with host
PORT = 6379
r = redis.Redis(host=HOST, port=PORT, decode_responses=False)
r.hgetall(b'<KEY>')[b'<FIELD>']
```

## Join unique lines by comma
```
python3 -c 'import sys; x = sys.stdin.read(); j = ",".join(set(x.split())); sys.stdout.write(j)'
```
## Deep compare jsons with nested json strings
Note the dependency - jsondiff.
```
import sys
import json
import pprint
from jsondiff import diff

def modified(v):
  if isinstance(v, list):
    return [modified(x) for x in v]
  if not isinstance(v, str):
    return v
  try:
    return json.loads(v, object_hook=hook)
  except:
    return v
def hook(pairs, **kwargs):
  return dict(
    sorted(
    {
      k: modified(v) for (k,v) in pairs.items()
    }.items(), 
    key=lambda x: x[0].lower())
  ) 
  
if __name__ == "__main__":
  with open(
    sys.argv[0], "r"
  ) as f, open(
    sys.argv[1], "r"
  ) as f2:
    x = json.load(f, object_hook=hook)
    x2 = json.load(f2, object_hook=hook)
    pprint.pprint(diff(x, x2))

```
