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

序号	|	模块	|	功能简述	|	请求方式	|	请求地址	|	后台响应方法
---|---|---|---|---|---
1	|	用户管理	|	返回当前登录用户的详细信息	|	GET	|	[/api/user](./用户管理.md/#1当前用户信息)	|	server.GetSelf
2	|	用户管理	|	返回用户对仓库的操作记录，如推送、合并分支等	|	GET	|	[/api/user/feed](./用户管理.md/#2当前用户操作仓库记录)	|	server.GetFeed
3	|	用户管理	|	返回当前用户所有开启了WebHook的仓库详细信息	|	GET	|	[/api/user/repos](./用户管理.md/#3所属当前用户的已开启WebHook的仓库信息)	|	server.GetRepos
4	|	用户管理	|	返回当前用户的所有仓库系信息	|	GET	|	[/api/user/repos/remote](./用户管理.md/#4所属当前用户的所有仓库信息)	|	server.GetRemoteRepos
5	|	用户管理	|	使当前token立即失效	|	DELETE	|	[/api/user/token](./用户管理.md/#5销毁当前用户token)	|	server.DeleteToken
6	|	用户管理	|	返回当前用户的token	|	POST	|	[/api/user/token](./用户管理.md/#6获取当前用户token)	|	server.PostToken
7	|	用户管理	|	返回所有活跃用户信息	|	GET	|	[/api/users](./用户管理.md/#7获取所有用户信息)	|	server.GetUsers
8	|	用户管理	|	创建一个新的账户，并返回该用户的详细信息	|	POST	|	[/api/users](./用户管理.md/#8创建用户)	|	server.PostUser
9	|	用户管理	|	删除指定的用户	|	DELETE	|	[/api/users/:login](./用户管理.md/#9删除指定用户)	|	server.DeleteUser
10	|	用户管理	|	获取指定用户的详细信息	|	GET	|	[/api/users/:login](./用户管理.md/#10获取指定用户信息)	|	server.GetUser
11	|	用户管理	|	更新用户信息	|	PATCH	|	[/api/users/:login](./用户管理.md/#11更新用户信息)	|	server.PatchUser
12	|	构建管理	|	查询当前正在进行构建的仓库信息	|	GET	|	[/api/builds](./构建管理.md/#1查询当前正在进行构建的仓库信息)	|	server.GetBuildQueue
13	|	构建管理	|	获取指定仓库构建信息	|	GET	|	[/api/repos/:owner/:name/builds](./构建管理.md/#2获取指定仓库构建信息)	|	server.GetBuilds
14	|	构建管理	|	获取指定仓库指定的构建信息	|	GET	|	[/api/repos/:owner/:name/builds/:number](./构建管理.md/#3获取指定仓库指定的构建信息)	|	server.GetBuild
15	|	构建管理	|	根据构建编号进行重新构建	|	POST	|	[/api/repos/:owner/:name/builds/:number](./构建管理.md/#4重新构建)	|	server.PostBuild
16	|	构建管理	|	根据构建编号和job编号取消指定的构建	|	DELETE	|	[/api/repos/:owner/:name/logs/:number/:job](./构建管理.md/#5取消指定的构建)	|	server.DeleteBuild
17	|	仓库管理	|	删除仓库构建信息	|	DELETE	|	[/api/repos/:owner/:name/builds/:number/:job](./仓库管理.md/#6删除仓库构建信息)	|	server.DeleteRepo
18	|	仓库管理	|	返回仓库详细信息	|	GET	|	[/api/repos/:owner/:name](./仓库管理.md/#1获取仓库信息)	|	server.GetRepo
19	|	仓库管理	|	更新仓库响应配置	|	PATCH	|	[/api/repos/:owner/:name](./仓库管理.md/#2更新仓库响应配置)	|	server.PatchRepo
20	|	仓库管理	|	激活仓库事件响应	|	POST	|	[/api/repos/:owner/:name](./仓库管理.md/#3激活仓库事件响应)	|	server.PostRepo
21	|	仓库管理	|	修改仓库拥有权【待测】	|	POST	|	[/api/repos/:owner/:name](./仓库管理.md/#4修改仓库拥有权)	|	server.ChownRepo
22	|	构建管理	|	获取构建时的所以构建日志	|	GET	|	[/api/repos/:owner/:name/chown](./构建管理.md/#5获取构建日志)	|	server.GetBuildLogs
23	|	secret管理	|	获取设置在仓库中的secret	|	GET	|	[/api/repos/:owner/:name/secrets](./secret管理.md/#1获取设置在仓库中的secret)	|	server.GetSecrets
24	|	secret管理	|	给指定仓库增加secret	|	POST	|	[/api/repos/:owner/:name/secrets](./secret管理.md/#2给指定仓库增加secret)	|	server.PostSecret
25	|	secret管理	|	删除仓库指定的secret	|	DELETE	|	[/api/repos/:owner/:name/secrets/:secret](./secret管理.md/#3删除仓库指定的secret)	|	server.DeleteSecret
26	|	secret管理	|	更新仓库secret【待测】	|	POST	|	[/api/repos/:owner/:name/sign](./secret管理.md/#4更新仓库secret)	|	server.Sign
27	|	secret管理	|	查询组织的secret	|	GET	|	[/api/teams/:team/secrets](./secret管理.md/#5查询组织的secret)	|	server.GetTeamSecrets
28	|	secret管理	|	增加组织的secret	|	POST	|	[/api/teams/:team/secrets](./secret管理.md/#6增加组织的secret)	|	server.PostTeamSecret
29	|	secret管理	|	删除组织的secret	|	DELETE	|	[/api/teams/:team/secrets/:secret](./secret管理.md/#7删除组织的secret)	|	server.DeleteTeamSecret
30	|	secret管理	|	查询全局secrets	|	GET	|	[/api/global/secrets](./secret管理.md/#8查询全局secrets)	|	server.GetGlobalSecrets
31	|	secret管理	|	增加全局secrets	|	POST	|	[/api/global/secrets](./secret管理.md/#9增加全局secrets)	|	server.PostGlobalSecret
32	|	secret管理	|	删除全局secrets	|	DELETE	|	[/api/global/secrets/:secret](./secret管理.md/#10删除全局secrets)	|	server.DeleteGlobalSecret
33	|	其它	|	api-agents【待测】	|	GET	|	[/api/agents](./其它.md/#1api-agents)	|	server.GetAgents
34	|	其它	|	查看CC-Menu	|	GET	|	[/api/badges/:owner/:name/cc.xml](./其它.md/#2查看CC-Menu)	|	server.GetCC
35	|	其它	|	获取构建徽章	|	GET	|	[/api/badges/:owner/:name/status.svg](./其它.md/#3获取构建徽章)	|	server.GetBadge
36	|	Debug	|	api-debug-pprof【待测】	|	GET	|	[/api/debug/pprof/](./Debug.md/#1api-debug-pprof)	|	server.IndexHandler.func1
37	|	Debug	|	api-debug-pprof-block【待测】	|	GET	|	[/api/debug/pprof/block](./Debug.md/#2api-debug-pprof-block)	|	server.BlockHandler.func1
38	|	Debug	|	api-debug-pprof-cmdline【待测】	|	GET	|	[/api/debug/pprof/cmdline](./Debug.md/#3api-debug-pprof-cmdline)	|	server.CmdlineHandler.func1
39	|	Debug	|	api-debug-pprof-goroutine【待测】	|	GET	|	[/api/debug/pprof/goroutine](./Debug.md/#4api-debug-pprof-goroutine)	|	server.GoroutineHandler.func1
40	|	Debug	|	api-debug-pprof-heap【待测】	|	GET	|	[/api/debug/pprof/heap](./Debug.md/#5api-debug-pprof-heap)	|	server.HeapHandler.func1
41	|	Debug	|	api-debug-pprof-profile【待测】	|	GET	|	[/api/debug/pprof/profile](./Debug.md/#6api-debug-pprof-profile)	|	server.ProfileHandler.func1
42	|	Debug	|	api-debug-pprof-symbol【待测】	|	GET	|	[/api/debug/pprof/symbol](./Debug.md/#7api-debug-pprof-symbol)	|	server.SymbolHandler.func1
43	|	Debug	|	api-debug-pprof-symbol【待测】	|	POST	|	[/api/debug/pprof/symbol](./Debug.md/#8api-debug-pprof-symbol)	|	server.SymbolHandler.func1
44	|	Debug	|	api-debug-pprof-threadcreate【待测】	|	GET	|	[/api/debug/pprof/threadcreate](./Debug.md/#9api-debug-pprof-threadcreate)	|	server.ThreadCreateHandler.func1
45	|	Debug	|	api-debug-pprof-trace【待测】	|	GET	|	[/api/debug/pprof/trace](./Debug.md/#10api-debug-pprof-trace)	|	server.TraceHandler.func1


