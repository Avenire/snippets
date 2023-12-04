## Text to json escaped string (OS X)
`jq -n --arg raw "$(pbpaste)" '$raw | @json'`

## Various filtering out from complex jsons
`jq 'del(.some.nested.keyForArray | .[] | (.doNotWantThat, .andDoNotWantThat))'`
### Example:
Input:
```
{
  "some": {
    "nested": {
      "keyForArray": [
        {
          "wantThat": "value",
          "andThat" : 123,
          "doNotWantThat": {},
          "andDoNotWantThat": "123"
        },
        {
          "wantThat": "value2",
          "andThat" : 1234,
          "doNotWantThat": [123],
          "andDoNotWantThat": "4321"
        }
      ]
    }
  }
}
```
Output:
```

{
  "some": {
    "nested": {
      "keyForArray": [
        {
          "wantThat": "value",
          "andThat": 123
        },
        {
          "wantThat": "value2",
          "andThat": 1234
        }
      ]
    }
  }
}
```
