## pay2.0  

### get amount which you need to deploy the app
- 请求方式: `post`
- 请求地址: `/v2alpha/{type}/acquire_pre_amount`  
type must be one of -->  USD | ANKR_ERC20  | USDT_ERC20  
USD is payment of CREDIT_CARD, others mean token payment
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




### create pre_card pay
- 请求方式: `post`
- 请求地址: `/v2alpha/teams/{team_id}/cards/{card_id}`
- 请求参数:  
```json
{
    "team_id" : "",
    "card_id" : "",
    "amount": "22.2",    "get from api /v2alpha/{type}/acquire_pre_amount"
    "period": 12,    "month you buy"
    "auto_renewal": 1     " if you need  auto_renewal, this value must be 1, otherwise it should be 0   自动续费设置成1"
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


