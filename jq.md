## Text to json escaped string (OS X)
`jq -n --arg raw "$(pbpaste)" '$raw | @json'`
