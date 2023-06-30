# prisma-client-go N+1 repro
## reproduction steps
```sh
go mod tidy
make generate
make reset-and-seed
make run-with-log
curl -X POST 'http://localhost:8080/graphql' -H 'content-type: application/json' -d '{"query":"query Hoge {\n  users {\n    id\n    name\n    posts {\n      id\n      title\n      content\n    }\n  }\n}","operationName":"Hoge"}'
```
