## pay2.0  crypto pay (ANKR_ERC20/USDT_ERC20)

## ETH crypto pay
### CreateApp
-  `post`
-  `/v2alpha/app/v2/app`  

- 请求参数:  
```json
{    
    "pre_pay_info": {
        "pay_method": "ANKR_ERC20",
        
     },
    "name": "xyh421--boinc-5",
    "cluster_id": "cls-a91a7dbc-1a23-42f6-a66f-876094349f03",
    "namespace_name": "123",
    "cpu_limit": 1000,
    "mem_limit": 2000,
    "storage_limit": 20000,
    "team_id": "32599514-1dc0-435b-ab8c-5b6e208ad481",
    "chart_name": "boinc",
    "chart_repo": "stable",
    "chart_ver": "0.1.1",
    "chart_desc": "BOINC Rosetta",
    "chart_icon_url": "https://assets.ankr.com/charts/BOINC.svg",
    "app_version": "0.1.0",
    "instance_type": "123",
    "enterprise": false,
    "custom_values": [
        {
            "key": "ankrCustomValues.ncpu",
            "value": "1"
        },
        {
            "key": "ankrCustomValues.account_key",
            "value": "70653ef37f742ab93761670734d12d9a"
        },
        {
            "key": "ankrCustomValues.email",
            "value": "123"
        },
        {
            "key": "ankrCustomValues.passwd",
            "value": "123"
        },
        {
            "key": "ankrCustomValues.username",
            "value": "123"
        }
    ]
}
```
- 响应内容:  
```json
{
   "amount": "33.3",
   "usd": "33.3"
}
if you pay with USD / USDT , amount is always equal to usd
```



