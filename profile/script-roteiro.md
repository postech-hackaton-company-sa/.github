---
runme:
  id: 01HSRT0KG2JD6Q0Q30R6RYXAK3
  version: v3
---

# Gerar o token do usuario

```sh {"id":"01HSRT5ZWKW8K6DZFWFVZSBB7G"}
curl -X POST "http://localhost:9080/realms/hackaton/protocol/openid-connect/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=password" \
  -d "client_id=hackaton" \
  -d "client_secret=yIOWvaD8hyh8gWz1Smqd2BQm2TehQ0UB" \
  -d "username=usuario-admin" \
  -d "password=123456789"
```

# API de ponto eletrônico

-> Cadastrar um ponto

```sh {"id":"01HSRT0KG2JD6Q0Q30QTTYWNTA"}
curl -X 'POST' \
  'http://localhost:8080/v1/ponto-eletronico' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJfQnZNc1lEaHl5VERqT0xsaWdheHg5M1hiOUdrZjJ4eFduX1FYZnlzRzlBIn0.eyJleHAiOjE3MTEzMjA3MDEsImlhdCI6MTcxMTMyMDQwMSwianRpIjoiZjQ1YWExMTItNTE2OS00NzdjLWE4ZjYtMGVlNmE5NzM3ZDdkIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDgwL3JlYWxtcy9oYWNrYXRvbiIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI0MzUxZjkxZS0xODg1LTQzNTUtOTFjYi1jYWYwNjgyYzAyZDAiLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJoYWNrYXRvbiIsInNlc3Npb25fc3RhdGUiOiJkNTEyY2JjOC0xMzYyLTQyNDgtYjRmMS0yOGVmNWYyNmNjNTkiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbIi8qIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJkZWZhdWx0LXJvbGVzLWhhY2thdG9uIiwib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiJdfSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJtYW5hZ2UtYWNjb3VudC1saW5rcyIsInZpZXctcHJvZmlsZSJdfX0sInNjb3BlIjoicHJvZmlsZSBlbWFpbCIsInNpZCI6ImQ1MTJjYmM4LTEzNjItNDI0OC1iNGYxLTI4ZWY1ZjI2Y2M1OSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJ1c3VhcmlvLWFkbWluIiwiZ2l2ZW5fbmFtZSI6IiIsImZhbWlseV9uYW1lIjoiIiwiZW1haWwiOiJkYW5pZWxtYXJpYWRhc2lsdmFAZ21haWwuY29tIn0.hUokGQCMEvCsktqJinVPYkrS-_6OuiHQRKk7VOJkr11sUaYln-C3sV2dfUhh5WRv4S7KwJv20I_8Kp5P6kbiJRDGPiS3nR3Wr41dOQvA33jzlN52zmi51gYGpWjpMxUoH_78wIgvSBfld3KY4GHWC1VWtNZWZO7hl7kxPe7ZYTbww7FVgEIi_pDSawEFL9WF6NDEmJ7DihmeE9yVhiqHMsO2Sguvrwpipvp_q6uXy3g793x8Wcl0wCTeiifnIp38qTXscFVPX0xmtF4ts_6C98uOZSdIgHFlme_L_b51jBkVGLZd8D_T6CteieIG93uCgK6TpXxZX-beP9Fb5hRwIQ' \
  -d ''
```

-> Cadastrar novamente, deve dar erro 400.

```sh {"id":"01HSRT0KG2JD6Q0Q30QW6M50XB"}
curl -X 'POST' \
  'http://localhost:8080/v1/ponto-eletronico' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJfQnZNc1lEaHl5VERqT0xsaWdheHg5M1hiOUdrZjJ4eFduX1FYZnlzRzlBIn0.eyJleHAiOjE3MTEzMjA3MDEsImlhdCI6MTcxMTMyMDQwMSwianRpIjoiZjQ1YWExMTItNTE2OS00NzdjLWE4ZjYtMGVlNmE5NzM3ZDdkIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDgwL3JlYWxtcy9oYWNrYXRvbiIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI0MzUxZjkxZS0xODg1LTQzNTUtOTFjYi1jYWYwNjgyYzAyZDAiLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJoYWNrYXRvbiIsInNlc3Npb25fc3RhdGUiOiJkNTEyY2JjOC0xMzYyLTQyNDgtYjRmMS0yOGVmNWYyNmNjNTkiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbIi8qIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJkZWZhdWx0LXJvbGVzLWhhY2thdG9uIiwib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiJdfSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJtYW5hZ2UtYWNjb3VudC1saW5rcyIsInZpZXctcHJvZmlsZSJdfX0sInNjb3BlIjoicHJvZmlsZSBlbWFpbCIsInNpZCI6ImQ1MTJjYmM4LTEzNjItNDI0OC1iNGYxLTI4ZWY1ZjI2Y2M1OSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJ1c3VhcmlvLWFkbWluIiwiZ2l2ZW5fbmFtZSI6IiIsImZhbWlseV9uYW1lIjoiIiwiZW1haWwiOiJkYW5pZWxtYXJpYWRhc2lsdmFAZ21haWwuY29tIn0.hUokGQCMEvCsktqJinVPYkrS-_6OuiHQRKk7VOJkr11sUaYln-C3sV2dfUhh5WRv4S7KwJv20I_8Kp5P6kbiJRDGPiS3nR3Wr41dOQvA33jzlN52zmi51gYGpWjpMxUoH_78wIgvSBfld3KY4GHWC1VWtNZWZO7hl7kxPe7ZYTbww7FVgEIi_pDSawEFL9WF6NDEmJ7DihmeE9yVhiqHMsO2Sguvrwpipvp_q6uXy3g793x8Wcl0wCTeiifnIp38qTXscFVPX0xmtF4ts_6C98uOZSdIgHFlme_L_b51jBkVGLZd8D_T6CteieIG93uCgK6TpXxZX-beP9Fb5hRwIQ' \
  -d ''
```

-> Verificar ponto do dia do usuario-admin

```sh {"id":"01HSRT0KG2JD6Q0Q30QZJN3VZ5"}
curl -X 'GET' \
  'http://localhost:8080/v1/ponto-eletronico?data=2024-03-01' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJfQnZNc1lEaHl5VERqT0xsaWdheHg5M1hiOUdrZjJ4eFduX1FYZnlzRzlBIn0.eyJleHAiOjE3MTEzMjE5MDksImlhdCI6MTcxMTMyMTYwOSwianRpIjoiZTI1MmIxZDUtY2M3Yy00ZGUzLTkzOWYtNDQyMTRmOWRmYTMyIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDgwL3JlYWxtcy9oYWNrYXRvbiIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI0MzUxZjkxZS0xODg1LTQzNTUtOTFjYi1jYWYwNjgyYzAyZDAiLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJoYWNrYXRvbiIsInNlc3Npb25fc3RhdGUiOiI0YTIwNmYxZi1mN2UxLTQ3NDYtOTI1My1hMjAzMzE2Mjg0MWMiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbIi8qIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJkZWZhdWx0LXJvbGVzLWhhY2thdG9uIiwib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiJdfSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJtYW5hZ2UtYWNjb3VudC1saW5rcyIsInZpZXctcHJvZmlsZSJdfX0sInNjb3BlIjoicHJvZmlsZSBlbWFpbCIsInNpZCI6IjRhMjA2ZjFmLWY3ZTEtNDc0Ni05MjUzLWEyMDMzMTYyODQxYyIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJ1c3VhcmlvLWFkbWluIiwiZ2l2ZW5fbmFtZSI6IiIsImZhbWlseV9uYW1lIjoiIiwiZW1haWwiOiJkYW5pZWxtYXJpYWRhc2lsdmFAZ21haWwuY29tIn0.VkGUk9zvwXQVLy7i9KTxxoN1aUdGBOhJoAmMdwgwVwnAb5sLpcwIRbVx_T4YQAn41dRpw9KkdbzpG1MhbAmClJOoMKJRC7zzr3RU6_1ao77yF7uQL95wxFKf2eUBqk70eFfiBGEUNCrlmdSWjGwiZo3C3yloj4P1a-KAfrMdXmTD-MsnRyRUVrGhWO5VM5_AtIeEeVGh_VPXZBWbDVKYu96EUj34V4fHiG3agk3xbzBW7hJUrleYehtouSSUkPamC1-Nn7iegIpiPWHtCvWJrUD-PjVCFsRpQSzZNV-oQSH53uP1rkPZr68UdE2FmfYcxa3LQAW0XLwY32nDuNDz7g' \
```

# API de funcionarios

-> Buscar dados

```sh {"id":"01HSRT0KG2JD6Q0Q30R3N3RZMR"}
curl -X 'GET' \
  'http://localhost:8080/v1/funcionarios?username=usuario-admin' \
  -H 'accept: */*' \
  -H 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJfQnZNc1lEaHl5VERqT0xsaWdheHg5M1hiOUdrZjJ4eFduX1FYZnlzRzlBIn0.eyJleHAiOjE3MTEzMjE5MDksImlhdCI6MTcxMTMyMTYwOSwianRpIjoiZTI1MmIxZDUtY2M3Yy00ZGUzLTkzOWYtNDQyMTRmOWRmYTMyIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDgwL3JlYWxtcy9oYWNrYXRvbiIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI0MzUxZjkxZS0xODg1LTQzNTUtOTFjYi1jYWYwNjgyYzAyZDAiLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJoYWNrYXRvbiIsInNlc3Npb25fc3RhdGUiOiI0YTIwNmYxZi1mN2UxLTQ3NDYtOTI1My1hMjAzMzE2Mjg0MWMiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbIi8qIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJkZWZhdWx0LXJvbGVzLWhhY2thdG9uIiwib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiJdfSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJtYW5hZ2UtYWNjb3VudC1saW5rcyIsInZpZXctcHJvZmlsZSJdfX0sInNjb3BlIjoicHJvZmlsZSBlbWFpbCIsInNpZCI6IjRhMjA2ZjFmLWY3ZTEtNDc0Ni05MjUzLWEyMDMzMTYyODQxYyIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJ1c3VhcmlvLWFkbWluIiwiZ2l2ZW5fbmFtZSI6IiIsImZhbWlseV9uYW1lIjoiIiwiZW1haWwiOiJkYW5pZWxtYXJpYWRhc2lsdmFAZ21haWwuY29tIn0.VkGUk9zvwXQVLy7i9KTxxoN1aUdGBOhJoAmMdwgwVwnAb5sLpcwIRbVx_T4YQAn41dRpw9KkdbzpG1MhbAmClJOoMKJRC7zzr3RU6_1ao77yF7uQL95wxFKf2eUBqk70eFfiBGEUNCrlmdSWjGwiZo3C3yloj4P1a-KAfrMdXmTD-MsnRyRUVrGhWO5VM5_AtIeEeVGh_VPXZBWbDVKYu96EUj34V4fHiG3agk3xbzBW7hJUrleYehtouSSUkPamC1-Nn7iegIpiPWHtCvWJrUD-PjVCFsRpQSzZNV-oQSH53uP1rkPZr68UdE2FmfYcxa3LQAW0XLwY32nDuNDz7g' \
```