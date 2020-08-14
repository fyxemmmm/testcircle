## pay2.0  


participant web前端
participant 支付服务
participant app服务
participant mysql serv
participant mongodb serv
participant stripe api

web前端->>支付服务:post app规格信息和购买时长(月)
#Note right of web前端:参数:月份
支付服务->>web前端:amount(需要支付的总金额)
web前端->>支付服务:post card_id、amount...
支付服务-->stripe api:信用卡扣费
stripe api-->支付服务:success
支付服务-->mysql serv:record
mysql serv-->支付服务:success
支付服务->>web前端:付款唯一标识(pay_id)
Note left of web前端:此时支付已成功
web前端->>app服务:deploy app...
app服务->>web前端:app_id
web前端->>支付服务:post app_id pay_id
支付服务-->mongodb serv:账单记录
mongodb serv-->支付服务:success
支付服务->>web前端:success
Note right of web前端:finish


### GetPreAmount
- 请求方式: `post`
- 请求地址: `/v2alpha/{type}/acquire_pre_amount`  
type must be one of -->  USD | ANKR_ERC20  | USDT_ERC20  
USD is payment of CREDIT_CARD, others mean token payment  
if you use CREDIT_CARD, then you should use USD
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
    "project_name": ""
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
                    "payment_method": "USD",    "if you use credit card, this is usd, other 2 enum -->   ANKR_ERC20 USDT_ERC20"
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




### GetPreInvoiceDetail
- 请求方式: `get`
- 请求地址: `/v2alpha/{team_id}/{pay_method}/{period}/invoice_detail`  
for example  
/v2alpha/{team_id}/CREDIT_CARD/2020-08-01/invoice_detail  
/v2alpha/{team_id}/ANKR_ERC20/2020-07-01/invoice_detail  
/v2alpha/{team_id}/USDT_ERC20/2020-08-01/invoice_detail  


- 响应内容:  
```json
{
    "total_amount": "22.3",
    "total_usd": "22.3",        "if you use credit_card -> usd , total_amount is always equal to total usd"
    "detail_list": [
        {
           "chart_name": "",
           "cpu_limit": 0,
           "mem_limit": 0,
           "storage_limit": 0,
           "amount": "12.3",
           "usd": "12.3", 
           "app_name":"",
           "icon_url": "",
           "app_start_time": "2020-08-01T08:00:00+08:00",
           "app_end_time": "2020-09-01T08:00:00+08:00"
       }
    ]
}
```


### GetRenewalList
- 请求方式: `get`
- 请求地址: `/v2alpha/{team_id}/get_renewal_list`  


- 响应内容:  
```json
{
    "prepayment_card_id": 12,
    "app_start_time": "2020-08-01T08:00:00+08:00",
    "app_end_time": "2020-09-01T08:00:00+08:00",
    "amount": "33.3",
    "auto_renewal": 1,    "1 means turn on the auto renewal"
    "app_name": "",
    "chart_name": "",
    "period": 3        "here period is the same meaning as month"
}
```



### EditAutoRenewalStatus
- 请求方式: `post`
- 请求地址: `/v2alpha/{team_id}/get_renewal_list`  

- 请求参数:  
```json
{
  "prepayment_card_id": 12,
  "auto_renewal": "CANCEL"    "must be CANCEL or AUTO_RENEWAL"
}
```
- 响应内容:  
```json
{
    "code": 0,
    "message": "success"
}
```
