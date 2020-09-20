## pay2.0  crypto pay (ANKR_ERC20/USDT_ERC20)

## ETH crypto pay
### CreateApp
-  `post`
-  `/v2alpha/app/v2/app`  
-  pre_pay_info.pay_method must be one of "ANKR_ERC20 or USDT_ERC20"

- request:  
```json
{    
    "pre_pay_info": {
        "pay_method": "ANKR_ERC20",
        "period": 3
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
- response:  
```json
    {
        "app_id": "xx"
    }
```



### GetEthOrder
-  `get`
-  `/v2alpha/teams/{team_id}/eth_order/{app_id}?pay_method=USDT_ERC20`  

- response:  
```json
    {
            "address": "0x111111111111",
            "value": "33.3"
    }
```





### CreateExtendOrder
-  `post`
-  `/v2alpha/create_extend_order`  

- request:  
```json
    {
            "app_id": "appidzzzxxkxkx",
            "period": "3",
            "pay_method": "CREDIT_CARD"
    }
```

- response:  
```json
    {
            "amount": "22.12"
    }
```




### ExtendAppAfterCreatingOrder
-  `post`
-  `/v2alpha/after_create_extend_order/do_extend_app`  

- request:  
```json
    {
            "app_id": "appidzzzxxkxkx",
            "period": "3",
            "pay_method": "CREDIT_CARD",
            "card_id": "cardidxzzzzzzxxx"
    }
```

- response:  
```json
    {
            "code": "22.12",
            "message": "success"
    }
```







### GetDepositList
-  `get`
-  `/v2alpha/teams/{team_id}/deposit_list`  

- response:  
```json
    {
            "deposit_list": [
                {
                    app_id : "xxxx",
                    deposit_time : 1598918400,
                    app_end_time : 1598918400,
                    usd : "33.3",
                    amount : "33.3",
                    project_name : "feixiang-bonic01",
                    chart_name : "bonic",
                    icon_url : "http://www.icon.xxxx",
                    pay_method : "CREDIT_CARD",
                    address : "0x2e2121121",
                    create_time : 1598918400,
                    app_run_time : 22,
                    app_total_time : 93,
                    transaction_hash : "xsajei231231313",
                    card_id : "cs13214214e"
                },
            
               {
                    app_id : "xxxx",
                    deposit_time : 1598918400,
                    app_end_time : 1598918400,
                    usd : "33.3",
                    amount : "33.3",
                    project_name : "feixiang-bonic01",
                    chart_name : "bonic",
                    icon_url : "http://www.icon.xxxx",
                    pay_method : "CREDIT_CARD",
                    address : "0x2e2121121",
                    create_time : 1598918400,
                    app_run_time : 22,
                    app_total_time : 93,
                    transaction_hash : "xsajei231231313",
                    card_id : "cs13214214e"
                }
            ]
          
    }
```




### ExtendApp
-  `get`
-  `/v2alpha/teams/{team_id}/extend_app`  
- if you want to extend the app which paid by credit_card, you should provice card_id

- request:  
```json
    {
        pay_method:"USDT_ERC20";
        app_id "XXXX";
        card_id:"";
    }
```

- response:  
```json
    {
            "code": 0,
            "message": "success"
    }
```



### PaymentList
-  `get`
-  `/v2alpha/{team_id}/pre_payment_list`  


- response:  
```json
[
    {
        "period": "2020-09-01",
        "total_usd": "33.33",
        "app_list": [
            {
                "app_id": "app_idcxzcxcx",
                "app_name": "myname",
                "chart_name": "bonic",
                "pay_method": "ANKR_ERC20",
                "usd": "33.2",
                "amount": "213",
                "billing_time": 1598918400,
                "icon_url": "http://www.icon.com"
            },
            {
                "app_id": "app_idcxzcxcx",
                "app_name": "myname",
                "chart_name": "bonic",
                "pay_method": "CREDIT_CARD",
                "usd": "33.2",
                "amount": "33.2",
                "billing_time": 1598918400,
                "icon_url": "http://www.icon.com"
            }
        ]
    },
    {
        "period": "2020-08-01",
        "total_usd": "33.33",
        "app_list": [
            {
                "app_id": "app_idcxzcxcx",
                "app_name": "myname",
                "chart_name": "bonic",
                "pay_method": "ANKR_ERC20",
                "usd": "33.2",
                "amount": "213",
                "billing_time": 1598918400,
                "icon_url": "http://www.icon.com"
            },
            {
                "app_id": "app_idcxzcxcx",
                "app_name": "myname",
                "chart_name": "bonic",
                "pay_method": "USDT_ERC20",
                "usd": "33.2",
                "amount": "213",
                "billing_time": 1598918400,
                "icon_url": "http://www.icon.com"
            }
        ]
    }
]
```


