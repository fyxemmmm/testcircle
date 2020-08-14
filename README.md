## pay2.0  

### GetPreAmount
- 请求方式: `post`
- 请求地址: `/v2alpha/{type}/acquire_pre_amount`  
type must be one of -->  USD | ANKR_ERC20  | USDT_ERC20  
USD is payment of CREDIT_CARD, others mean token payment  
CREDIT_CARD use USD
- 请求参数:  
```json
{
    "cluster_id" : "",
    "chart_name" : "",
    "cpu_limit": 100,
    "mem_limit": 100,
    "storage_limit": 100,
    "period": 3
}
period is between 1 ~ 12 , the same meaning as month, the month you buy
```
- 响应内容:  
```json
{
   "amount": "33.3",
   "usd": "33.3"
}
if you pay with USD / USDT , amount is always equal to usd
```




### CreatePrePaymentCard
- 请求方式: `post`
- 请求地址: `/v2alpha/teams/{team_id}/cards/{card_id}`
- 请求参数:  
```json
{
    "team_id" : "",
    "card_id" : "",
    "amount": "22.2",       "get from api /v2alpha/{type}/acquire_pre_amount"
    "period": 12,           "month you buy"
    "auto_renewal": 1       "if you need  auto_renewal, this value must be 1, otherwise it should be 0   自动续费设置成1"
}
```

- 响应内容:  
```json
{
    "code": 0,
    "message": "success",
    "pre_pay_id": 12
}
pre_pay_id  is very important because it will be used soon
```



### CallBackAppInfo
- 请求方式: `post`
- 请求地址: `/v2alpha/{type}/callback_app_info`  
type must be one of -->  USD | ANKR_ERC20  | USDT_ERC20  
CREDIT_CARD use USD
- 请求参数:  
```json
{
    "app_id" : "",
    "pre_pay_id" : 12,      "from api /v2alpha/teams/{team_id}/cards/{card_id}"
    "cluster_id": "",      
    "chart_name": "",        
    "cpu_limit": 0,
    "mem_limit": 0,
    "storage_limit": 0,
    "icon_url" : "",
    "project_name"： ""
}
```

- 响应内容:  
```json
{
    "code": 0,
    "message": "success"
}
```



### GetPreInvoiceList
- 请求方式: `get`
- 请求地址: `/v2alpha/{team_id}/invoice_list`  

- 响应内容:  
```json
{
    "invoice_list": [
        {
            "period": "2020-08-01",
            "total_usd" : "32.12",
            "icon_url_list": [
                {"icon_url": "xxxx"},
                {"icon_url": "yyyyy"},
            ],
            "info": [
                {
                    "period":  "2020-08-01",
                    "payment_method": "USD",    "if you use credit card, this is usd, other 2 enum --> USDT 、 ANKR"
                    "total_usd": "22.2",
                    "total_amount": "22.2",
                    "icon_url_list": [
                        {"icon_url": "xxxx"},
                        {"icon_url": "yyyyy"}
                    ]
                }
            ]
        }
    
    ]
}
```

