# secret管理

### 1、获取设置在仓库中的secret

> - 需要用户授权验证。

- 请求方式
```
GET /api/repos/:owner/:name/secrets
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk"  "http://192.168.56.21/api/repos/adminuser/drone-test/secrets"
```
  - 响应
```
Status: 200 OK
Content-Type: application/json; charset=utf-8
```
```
[
  {
    "id": 23,
    "name": "DOCKER_USERNAME",
    "value": "",
    "image": [
      "plugins/docker"
    ],
    "event": [
      "push",
      "tag",
      "deployment"
    ],
    "skip_verify": false,
    "conceal": false
  },
  {
    "id": 24,
    "name": "DOCKER_PASSWORD",
    "value": "",
    "image": [
      "plugins/docker"
    ],
    "event": [
      "push",
      "tag",
      "deployment"
    ],
    "skip_verify": false,
    "conceal": false
  }
]
```

### 2、给指定仓库增加secret

> - 需要用户授权验证。

- 请求方式
```
POST /api/repos/:owner/:name/secrets
```
  - 例子
```
curl -X POST -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" -H "Content-Type: application/json"  -d '    {
    "name": "drone",
    "value": "drone",
    "image": [
      "plugins/docker"
    ],
    "event": [
      "push",
      "tag",
      "deployment"
    ],
    "skip_verify": false,
    "conceal": false
    }' "http://192.168.56.21/api/repos/adminuser/drone-test/secrets"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```

### 3、删除仓库指定的secret

> - 需要用户授权验证。

- 请求方式
```
DELETE  /api/repos/:owner/:name/secrets/:secret
```
  - 例子
```
curl -X DELETE -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/repos/adminuser/drone-test/secrets/handhand"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```

### 4、更新仓库secret

> - 需要用户授权验证。

- 请求方式
```
POST /api/repos/:owner/:name/sign
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 5、查询组织的secret

> - 需要用户授权验证。

- 请求方式
```
GET	/api/teams/:team/secrets
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 6、增加组织的secret

> - 需要用户授权验证。

- 请求方式
```
POST	/api/teams/:team/secrets
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 7、secret管理

> - 需要用户授权验证。

- 请求方式
```
DELETE	/api/teams/:team/secrets/:secret
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 8、查询全局secrets

> - 需要用户授权验证。

- 请求方式
```
GET	/api/global/secrets
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 9、增加全局secrets

> - 需要用户授权验证。

- 请求方式
```
POST	/api/global/secrets
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```

### 10、删除全局secrets

> - 需要用户授权验证。

- 请求方式
```
DELETE	/api/global/secrets/:secret
```
  - 例子
```
待测
```
  - 响应
```
待测
```
```
待测
```