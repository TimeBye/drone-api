# API概述：
---
Drone提供了一个全面的API，用于与Drone服务器交互。文档的此部分提供了用于验证和使用远程API的说明。

### 官方库

Drone提供以下官方库用于与API集成：

| 语言 | 项目地址 |
| :---:| --- |
|Go | [https://github.com/drone/drone-go](https://github.com/drone/drone-go) |
|Node| [https://github.com/drone/drone-node](https://github.com/drone/drone-node) |

### 验证

- Drone使用`tokens`进行身份验证。您可以从Drone用户界面中`Account
`菜单` SHOW TOKEN`显示您的用户`tokens`。您可以在`http`的`Headers`中添加`Authorization`属性提供`tokens`：
- 后期需要用户验证的API我们以这种形式进行说明。
```
Authorization:{tokens}
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.p2KhqJ-hl7lVdWawKtowBucWRANmYLv6ZqY64-gE660" "http://192.168.56.21/api/user"
```
  - 响应
```
Status: 200 OK
Content-Type: application/json
```
```
{
  "id": 1,
  "login": "adminuser",
  "email": "ziling.zhong@hand-china.com",
  "avatar_url": "https://secure.gravatar.com/avatar/0f656b0b09d16bafa95064e7e9bd83bc",
  "active": false,
  "admin": true
}
```
- 或者使用`access_token`做为查询参数：
```
http://drone.com/api/user?access_token={tokens}
```
  - 例子
```
curl -X GET "http://192.168.56.21/api/user?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.p2KhqJ-hl7lVdWawKtowBucWRANmYLv6ZqY64-gE660"
```
  - 响应
```
Status: 200 OK
Content-Type: application/json
```
```
{
  "id": 1,
  "login": "adminuser",
  "email": "ziling.zhong@hand-china.com",
  "avatar_url": "https://secure.gravatar.com/avatar/0f656b0b09d16bafa95064e7e9bd83bc",
  "active": false,
  "admin": true
}
```

### API索引

序号	|	模块	|	功能简述	|	请求方式	|	请求地址	|	详细描述	|	后台响应方法
---|---|---|---|---|---|---
1	|	用户管理	|	当前用户信息	|	GET	|	[/api/user](./当前用户信息.md/#操作仓库记录 )	|	获取当前登录用户的详细信息	|	github.com/drone/drone/server.GetSelf
2	|	用户管理	|	当前用户操作仓库记录	|	GET	|	[/api/user/feed]( )	|	0	|	github.com/drone/drone/server.GetFeed
3	|	用户管理	|	所属当前用户的已开启WebHook的仓库信息	|	GET	|	[/api/user/repos]( )	|	0	|	github.com/drone/drone/server.GetRepos
4	|	用户管理	|	所属当前用户的所有仓库信息	|	GET	|	[/api/user/repos/remote]( )	|	0	|	github.com/drone/drone/server.GetRemoteRepos
5	|	用户管理	|	销毁当前用户token	|	DELETE	|	[/api/user/token]( )	|	0	|	github.com/drone/drone/server.DeleteToken
6	|	用户管理	|	获取当前用户token	|	POST	|	[/api/user/token]( )	|	0	|	github.com/drone/drone/server.PostToken
7	|	用户管理	|	获取所有用户信息	|	GET	|	[/api/users]( )	|	0	|	github.com/drone/drone/server.GetUsers
8	|	用户管理	|	创建用户	|	POST	|	[/api/users]( )	|	0	|	github.com/drone/drone/server.PostUser
9	|	用户管理	|	删除指定用户	|	DELETE	|	[/api/users/:login]( )	|	0	|	github.com/drone/drone/server.DeleteUser
10	|	用户管理	|	获取指定用户信息	|	GET	|	[/api/users/:login]( )	|	0	|	github.com/drone/drone/server.GetUser
11	|	用户管理	|	更新用户信息	|	PATCH	|	[/api/users/:login]( )	|	0	|	github.com/drone/drone/server.PatchUser
12	|	构建管理	|	查询当前正在构建仓库信息	|	GET	|	[/api/builds]( )	|	0	|	github.com/drone/drone/server.GetBuildQueue
13	|	构建管理	|	获取仓库构建信息	|	GET	|	[/api/repos/:owner/:name/builds]( )	|	0	|	github.com/drone/drone/server.GetBuilds
14	|	构建管理	|	获取指定构建信息	|	GET	|	[/api/repos/:owner/:name/builds/:number]( )	|	0	|	github.com/drone/drone/server.GetBuild
15	|	构建管理	|	重新构建	|	POST	|	[/api/repos/:owner/:name/builds/:number]( )	|	0	|	github.com/drone/drone/server.PostBuild
16	|	构建管理	|	取消指定的构建	|	DELETE	|	[/api/repos/:owner/:name/builds/:number/:job]( )	|	0	|	github.com/drone/drone/server.DeleteBuild
17	|	仓库管理	|	删除仓库构建信息	|	DELETE	|	[/api/repos/:owner/:name]( )	|	0	|	github.com/drone/drone/server.DeleteRepo
18	|	仓库管理	|	获取仓库信息	|	GET	|	[/api/repos/:owner/:name]( )	|	0	|	github.com/drone/drone/server.GetRepo
19	|	仓库管理	|	更新仓库响应配置	|	PATCH	|	[/api/repos/:owner/:name]( )	|	0	|	github.com/drone/drone/server.PatchRepo
20	|	仓库管理	|	激活仓库事件响应	|	POST	|	[/api/repos/:owner/:name]( )	|	0	|	github.com/drone/drone/server.PostRepo
21	|	仓库管理	|	0	|	POST	|	[/api/repos/:owner/:name/chown]( )	|	0	|	github.com/drone/drone/server.ChownRepo
22	|	仓库管理	|	获取构建日志	|	GET	|	[/api/repos/:owner/:name/logs/:number/:job]( )	|	0	|	github.com/drone/drone/server.GetBuildLogs
23	|	仓库管理	|	获取设置在仓库中的secret	|	GET	|	[/api/repos/:owner/:name/secrets]( )	|	0	|	github.com/drone/drone/server.GetSecrets
24	|	仓库管理	|	给指定仓库增加secret	|	POST	|	[/api/repos/:owner/:name/secrets]( )	|	0	|	github.com/drone/drone/server.PostSecret
25	|	仓库管理	|	删除仓库指定的secret	|	DELETE	|	[/api/repos/:owner/:name/secrets/:secret]( )	|	0	|	github.com/drone/drone/server.DeleteSecret
26	|	仓库管理	|	更新仓库secret	|	POST	|	[/api/repos/:owner/:name/sign]( )	|	0	|	github.com/drone/drone/server.Sign
27	|	组织secret	|	查询组织的secret	|	GET	|	[/api/teams/:team/secrets]( )	|	0	|	github.com/drone/drone/server.GetTeamSecrets
28	|	组织secret	|	增加组织的secret	|	POST	|	[/api/teams/:team/secrets]( )	|	0	|	github.com/drone/drone/server.PostTeamSecret
29	|	组织secret	|	删除组织的secret	|	DELETE	|	[/api/teams/:team/secrets/:secret]( )	|	0	|	github.com/drone/drone/server.DeleteTeamSecret
30	|	全局secret	|	查询全局secrets	|	GET	|	[/api/global/secrets]( )	|	0	|	github.com/drone/drone/server.GetGlobalSecrets
31	|	全局secret	|	增加全局secrets	|	POST	|	[/api/global/secrets]( )	|	0	|	github.com/drone/drone/server.PostGlobalSecret
32	|	全局secret	|	删除全局secrets	|	DELETE	|	[/api/global/secrets/:secret]( )	|	0	|	github.com/drone/drone/server.DeleteGlobalSecret
33	|	0	|	0	|	GET	|	[/api/agents]( )	|	0	|	github.com/drone/drone/server.GetAgents
34	|	0	|	查看CC Menu	|	GET	|	[/api/badges/:owner/:name/cc.xml]( )	|	0	|	github.com/drone/drone/server.GetCC
35	|	0	|	获取构建徽章	|	GET	|	[/api/badges/:owner/:name/status.svg]( )	|	0	|	github.com/drone/drone/server.GetBadge
36	|	Debug	|	0	|	GET	|	[/api/debug/pprof/]( )	|	0	|	github.com/drone/drone/server.IndexHandler.func1
37	|	Debug	|	0	|	GET	|	[/api/debug/pprof/block]( )	|	0	|	github.com/drone/drone/server.BlockHandler.func1
38	|	Debug	|	0	|	GET	|	[/api/debug/pprof/cmdline]( )	|	0	|	github.com/drone/drone/server.CmdlineHandler.func1
39	|	Debug	|	0	|	GET	|	[/api/debug/pprof/goroutine]( )	|	0	|	github.com/drone/drone/server.GoroutineHandler.func1
40	|	Debug	|	0	|	GET	|	[/api/debug/pprof/heap]( )	|	0	|	github.com/drone/drone/server.HeapHandler.func1
41	|	Debug	|	0	|	GET	|	[/api/debug/pprof/profile]( )	|	0	|	github.com/drone/drone/server.ProfileHandler.func1
42	|	Debug	|	0	|	GET	|	[/api/debug/pprof/symbol]( )	|	0	|	github.com/drone/drone/server.SymbolHandler.func1
43	|	Debug	|	0	|	POST	|	[/api/debug/pprof/symbol]( )	|	0	|	github.com/drone/drone/server.SymbolHandler.func1
44	|	Debug	|	0	|	GET	|	[/api/debug/pprof/threadcreate]( )	|	0	|	github.com/drone/drone/server.ThreadCreateHandler.func1
45	|	Debug	|	0	|	GET	|	[/api/debug/pprof/trace]( )	|	0	|	github.com/drone/drone/server.TraceHandler.func1
