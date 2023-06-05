# Minimal JWT/JWKS server for testing purposes

## Usage

### Start server

Install Elixir and Erlang. Then:

```bash
mix deps.get
mix run --no-halt
```

### JWKS endpoint

```bash
curl 'http://127.0.0.1:4001/keys.json'
{"keys":[{"e":"AQAB","kid":"testkey@emqx.io","kty":"RSA","n":"cD5oaT4P_Qn1kCPe1AgC8NOdG9k0XQh5pOYlwGijGxjpl7w8YVJAn_4Ql_WLV98TF5ogf313efDIGyk2WKGigYe9NUN5iy7Xke3GmqKDUv_4ymFtmUUKUNe3NXT4Z5kaip6WgcBeS7dDOT6EzFE5qUW0f7wY2n7-PbKKvVn0TbE"}]}
```

### Exchange login/password for RS-encoded JWT

Logins and passwords are hardcoded in [`lib/jwt_server.ex`](lib/jwt_server.ex).

```bash
curl -X POST 'http://127.0.0.1:4001/rs/authn_acl_token' -d "username=pubuser&password=pass1"
eyJhbGciOiJSUzI1NiIsImtpZCI6InRlc3RrZXlAZW1xeC5pbyJ9.eyJhY2wiOnsicHViIjpbImZvbyJdfSwiZXhwIjoxNjg1OTY1ODMyLCJpYXQiOjE2ODU5NjUyMzIsInVzZXJuYW1lIjoicHVidXNlciJ9.Pr6cn1a6GetMxs-WdV5CpJ2dx2xHYRR7X951t49ycEKupKwiiaCgSnZ6jwI2gP_QjJIVZnx3vaI-w-g6k0OihPZg0QVhqjSlW1TSrtNoha42balhst9rNWlTFQQU20DdDnRdMvDapCBH82ALTCpmdKUQVptZPqJ8ZCI9xVChqaU
```

### Exchange login/password for HS-encoded JWT

```bash
curl -X POST 'http://127.0.0.1:4001/hs/authn_acl_token' -d "username=pubuser&password=pass1"
eyJhbGciOiJIUzI1NiJ9.eyJhY2wiOnsicHViIjpbImZvbyJdfSwiZXhwIjoxNjg1OTY1ODM5LCJpYXQiOjE2ODU5NjUyMzksInVzZXJuYW1lIjoicHVidXNlciJ9.p8tsFtx1Wt2TGYKVOaJiYaE5qsTVPBTCBVhxzkB_a_Q
```
