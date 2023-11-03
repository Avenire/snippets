## Follow redirects, pass authentication details
Without --location-trusted curl will strip Authorization header.
`curl  -H 'Authorization: Bearer <secret>' -L --location-trusted`
