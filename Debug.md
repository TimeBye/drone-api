# Debug
---

### 1、api-debug-pprof

> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof"
```
  - 响应
```
Status: 200 OK
Content-Type: text/html; charset=utf-8
```
```
<html>
    <head>
        <title>/debug/pprof/</title>
    </head>
    <body>
        /debug/pprof/<br>
        <br>
        profiles:<br>
        <table>
            <tr><td align=right>0<td><a href="block?debug=1">block</a>
            <tr><td align=right>16<td><a href="goroutine?debug=1">goroutine</a>
            <tr><td align=right>6<td><a href="heap?debug=1">heap</a>
            <tr><td align=right>8<td><a href="threadcreate?debug=1">threadcreate</a>
        </table>
        <br>
        <a href="goroutine?debug=2">full goroutine stack dump</a><br>
    </body>
</html>

```

### 2、api-debug-pprof-block


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/block
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/block"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
--- contention:
cycles/second=2494244678
```


### 3、api-debug-pprof-cmdline


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/cmdline
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/cmdline"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
/drone�server
```


### 4、api-debug-pprof-goroutine


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/goroutine
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/goroutine"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
goroutine profile: total 17
1 @ 0xa93598 0xa93373 0xa8ec64 0x8d69fe 0x8d7056 0x7cb2a0 0x79ae9a 0x7b2616 0x79ae9a 0x7b2e3d 0x79ae9a 0x7b23e5 0x79ae9a 0x5ba973 0x79ae9a 0x5c313c 0x79ae9a 0x7af314 0x79ae9a 0x7af150 0x79ae9a 0x7ac4b1 0x79ae9a 0x7a1af2 0x7a1727 0x5877fe 0x58404e 0x47fd01
1 @ 0x44f2f3 0x449c9e 0x449160 0x6b253a 0x6b25a6 0x6b623c 0x6d4a2d 0x588ae1 0x587b49 0x587996 0x588098 0x4127e1 0x416235 0x4c3058 0x4bf991 0x40d92b 0x44ef10 0x47fd01
1 @ 0x47fd01
1 @ 0x42f5de 0x462702 0x517338 0x47fd01
1 @ 0x44f2f3 0x44f3b4 0x4254ff 0x42504b 0x7d7be3 0x7d8d2a 0x7dbbdf 0x8f3052 0x8f3204 0x7d8f1e 0x7b440e 0x79ae9a 0x7b2d77 0x79ae9a 0x7b23e5 0x79ae9a 0x5ba973 0x79ae9a 0x5c313c 0x79ae9a 0x7af314 0x79ae9a 0x7af150 0x79ae9a 0x7ac4b1 0x79ae9a 0x7a1af2 0x7a1727 0x5877fe 0x58404e 0x47fd01
1 @ 0x44f2f3 0x44f3b4 0x4254ff 0x42504b 0x9de9e5 0x47fd01
1 @ 0x44f2f3 0x44f3b4 0x4254ff 0x42504b 0x7d7be3 0x7dbc7c 0x47fd01
1 @ 0x44f2f3 0x449c9e 0x449160 0x6b253a 0x6b25a6 0x6b43fa 0x6c90e4 0x57d856 0x76e5a9 0x76f41a 0x76f493 0x784301 0x784070 0x576e66 0x57f059 0x583a67 0x47fd01
2 @ 0x44f2f3 0x449c9e 0x449160 0x6b253a 0x6b25a6 0x6b43fa 0x6c90e4 0x59a897 0x5b0f10 0x76e5a9 0x76e7cc 0x596db7 0x47fd01
1 @ 0x44f2f3 0x44f3b4 0x4254ff 0x42504b 0x710148 0x47fd01
1 @ 0x44f2f3 0x449c9e 0x449160 0x6b253a 0x6b25a6 0x6b43fa 0x6c90e4 0x57d856 0x76e5a9 0x76ee1a 0x8ed19e 0x8f3364 0x76e5a9 0x76f41a 0x76f759 0x711547 0x47fd01
1 @ 0x44f2f3 0x45e017 0x45d572 0x711c18 0x47fd01
1 @ 0x44f2f3 0x449c9e 0x449160 0x6b253a 0x6b25a6 0x6b43fa 0x6c90e4 0x76e5a9 0x76ec20 0x8dc5d9 0x8dc829 0x8ddfc0 0x8de9f5 0x7c744c 0x7c716b 0x79ae9a 0x7b2e3d 0x79ae9a 0x7b23e5 0x79ae9a 0x5ba973 0x79ae9a 0x5c313c 0x79ae9a 0x7af314 0x79ae9a 0x7af150 0x79ae9a 0x7ac4b1 0x79ae9a 0x7a1af2 0x7a1727
2 @ 0x44f2f3 0x45e017 0x45d572 0x598802 0x47fd01
1 @ 0x44f2f3 0x45e017 0x45d572 0x7cc5ed 0x47fd01
```

### 5、api-debug-pprof-heap


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/heap
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/heap"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
heap profile: 0: 0 [7: 45392] @ heap/1048576
0: 0 [1: 32] @ 0x4673c7 0x46724f 0x9da0dc 0x9e723a 0x984825 0x985e89 0x985f8d 0x97bc7c 0x97bd55 0x80eb0e 0x805400 0x7b1f4b 0x7d41c4 0x8e84e3 0x7d330c 0x7d37a3 0x7b2100 0x79ae9a 0x5ba973 0x79ae9a 0x5c313c 0x79ae9a 0x7af314 0x79ae9a 0x7af150 0x79ae9a 0x7ac4b1 0x79ae9a 0x7a1af2 0x7a1727 0x5877fe 0x58404e
0: 0 [1: 288] @ 0x429a94 0x42bd1f 0x610219 0x64a514 0x647f31 0x647036 0x646b7b 0x8e7e70 0x7d330c 0x7d37a3 0x7b2100 0x79ae9a 0x5ba973 0x79ae9a 0x5c313c 0x79ae9a 0x7af314 0x79ae9a 0x7af150 0x79ae9a 0x7ac4b1 0x79ae9a 0x7a1af2 0x7a1727 0x5877fe 0x58404e 0x47fd01
0: 0 [2: 8192] @ 0x462b25 0x771487 0xa9f63d 0xa9fdc5 0x9f6448 0x9f60ed 0x9f9633 0x9f6f7e 0x9f6756 0x9f6675 0x80d8ec 0x80d4a5 0x80cf4f 0x5b9ce3 0x5b9ba5 0x41241f 0x416235 0x4c3058 0x4bf991 0x40d92b 0x44ef10 0x47fd01
0: 0 [1: 4096] @ 0x462b25 0x771487 0xa9f63d 0xa9fdc5 0x9f64c7 0x9f60ed 0x9f9633 0x9f6f7e 0x9f6756 0x9f6675 0x80d8ec 0x80d4a5 0x80cf4f 0x5b9ce3 0x5b9ba5 0x41241f 0x416235 0x4c3058 0x4bf991 0x40d92b 0x44ef10 0x47fd01
0: 0 [1: 32768] @ 0x8ba13c 0x78ac3d 0x789647 0x9e9f1b 0x9eb4a1 0x9eb529 0x9f1375 0x9f5fae 0x9f9633 0x9f6f7e 0x9f6756 0x9f6675 0x80d8ec 0x80d4a5 0x80cf4f 0x5b9ce3 0x5b9ba5 0x41241f 0x416235 0x4c3058 0x4bf991 0x40d92b 0x44ef10 0x47fd01
0: 0 [1: 16] @ 0x7895a2 0x9e9f1b 0x9ead61 0x9eade9 0x9f1375 0x9f5fae 0x9f9633 0x9f6f7e 0x9f6756 0x9f6675 0x80d8ec 0x80d4a5 0x80cf4f 0x5b9ce3 0x5b9ba5 0x41241f 0x416235 0x4c3058 0x4bf991 0x40d92b 0x44ef10 0x47fd01

# runtime.MemStats
# Alloc = 997464
# TotalAlloc = 6552248
# Sys = 7706872
# Lookups = 360
# Mallocs = 64381
# Frees = 56268
# HeapAlloc = 997464
# HeapSys = 4784128
# HeapIdle = 2629632
# HeapInuse = 2154496
# HeapReleased = 2490368
# HeapObjects = 8113
# Stack = 458752 / 458752
# MSpan = 30480 / 49152
# MCache = 2400 / 16384
# BuckHashSys = 1445118
# NextGC = 4194304
# PauseNs = [1358256 271752 724918 3573667 136058 110708 257656 161978 110745 885638 193968 114214 742072 93676 976530 86654 4874582 2007032 231615 127757 171425 161195 124669 1426162 94568 1068911 189235 124775 202014 178505 120382 594140 174515 122961 98778 95858 232695 102653 176036 107800 230215 746730 541480 177664 1045550 906115 169555 204877 133448 3560583 232052 81373 98015 164173 142994 922568 114577 83949 87960 85637 184080 165213 193692 448952 223118 95047 95329 9209815 5938173 228334 122241 3071823 3431233 201726 100174 82612 3365410 99784 94921 738390 197034 177946 978877 119382 148623 94108 1206938 82668 116792 150878 92452 146132 108081 136572 1531378 4123761 118563 100101 422924 224746 256816 172594 80974 168798 5909242 1248944 1166887 332232 156735 332698 163779 265858 363986 99041 111643 157576 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0]
# NumGC = 116
# EnableGC = true
# DebugGC = false
```


### 6、api-debug-pprof-profile


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/profile
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/profile"
```
  - 响应
```
Status: 200 OK
Content-Type: application/octet-stream
```
```
#下载了一个名为profile的二进制文件
```


### 7、api-debug-pprof-symbol


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/symbol
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/symbol"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
num_symbols: 1
```

### 8、api-debug-pprof-symbol


> - 需要用户授权验证。

- 请求方式
```
POST	/api/debug/pprof/symbol
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
```


### 9、api-debug-pprof-threadcreate


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/threadcreate
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/threadcreate"
```
  - 响应
```
Status: 200 OK
Content-Type: text/plain; charset=utf-8
```
```
threadcreate profile: total 8
8 @
```


### 10、api-debug-pprof-trace


> - 需要用户授权验证。

- 请求方式
```
GET	/api/debug/pprof/trace
```
  - 例子
```
curl -X GET -H "Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZXh0IjoiYWRtaW51c2VyIiwidHlwZSI6InVzZXIifQ.HvnfTlVqdGneN76HqvluLQSs9LlGqCImBalrppIK7Sk" "http://192.168.56.21/api/debug/pprof/trace"
```
  - 响应
```
Status: 200 OK
Content-Type: application/octet-stream
```
```
#下载了一个名为trace的二进制文件
```