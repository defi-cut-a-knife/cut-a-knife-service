## user login service
Users can access the system to receive red envelope activities

GET /user/login?username=xxx&signature=xxx
username: Your wallet account address
response: json data and user cookie
200 OK
{"status": 200, "message": "login success", "data": {"airdrop": "200", "token_name": "Knife", "already_obtaied": "197", "remaining_draws": 3, "expire_time": 1728998093}}
expire_time: 24 hours later
airdrop: Number of airdrops. eg: 200、500、1000
already_obtaied: Number of airdrops already obtained. eg: 197、490、950
token_name: Token name. eg: Knife、Cake、Sword
remaining_draws: Remaining attempts at lottery draw

403 Forbidden
{"status": 403, "message": "Contract address is not allowed to participate in activities"}
ps: Contract addresses are not allowed to participate in activities

Set-Cookie: knife_cookie=xxx; Expires=xxxx; Path=/; Secure; HttpOnly


## get a link to a friend's assistance
Users can obtain a red envelope assistance link，

GET /user/get_link?username=xxx

Cookie: knife_cookie=xxx

username: Your wallet account address
response: json data and user cookie
200 OK
{"status": 200, "message": "get link success", "data": {"link": "https://domain/user/assist?assisted_username=xxx"}}
expire_time: 24 hours later
airdrop: Number of airdrops. eg: 200、500、1000
already_obtaied: Number of airdrops already obtained. eg: 197、490、950
token_name: Token name. eg: Knife、Cake、Sword
remaining_draws: Remaining attempts at lottery draw

401 Unauthorized
{"status": 401, "message": "Please participate in activities first"}
ps: User must participate in activities first

403 Forbidden
{"status": 403, "message": "Contract address is not allowed to participate in activities"}
ps: Contract addresses are not allowed to participate in activities

408 Request Timeout
{"status": 408, "message": "Activitie timeout, please try again"}

## 