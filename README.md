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
- 请求地址: `goods-specifications`
- 请求参数:  
```json

```

- 响应内容:  
```json
{
    "code": 1,
    "message": "success",
    "info": ""
}
```


### 规格更新
- 请求方式: `post`
- 请求地址: `goods-specification/update-sp`
- 请求参数:  
```json
{
	"goods_id": 1,
	"main_specification_name": "颜色1",
	"second_specification_name": "鞋码1",
	"specification": [
		{
			"main_specification": "蓝色",
			"second_specification": "37",
			"purchasing_cost": 23
		},
		{
			"main_specification": "蓝色",
			"second_specification": "38",
			"purchasing_cost": 24
		},
		{
			"main_specification": "蓝色",
			"second_specification": "39",
			"purchasing_cost": 21
		},
		{
			"main_specification": "绿色",
			"second_specification": "37",
			"purchasing_cost": 23
		},
		{
			"main_specification": "绿色",
			"second_specification": "42",
			"purchasing_cost": 21
		}
	],
	"pics": [
		{
			"main_specification": "蓝色",
			"image_url": "https://www.baidu.com2"
		},
		{
			"main_specification": "绿色",
			"image_url": "https://www.baidu.com3"
		}
	]
}
```

- 响应内容:  
```json
{
    "code": 1,
    "message": "success",
    "info": ""
}
```




### 规格详情
- 请求方式: `post`
- 请求地址: `goods-specifications?goods_id=1`
- 请求参数:  

- 响应内容:  
```json
{
    "code": 1,
    "message": "success",
    "info": {
        "goods_id": "1",
        "main_specification_name": "颜色",
        "second_specification_name": "鞋码",
        "specification": [
            {
                "main_specification": "蓝色",
                "second_specification": "37",
                "purchasing_cost": "23.00",
                "original_cost": "33.41",   // 仅仅是展示用
                "after_discount_cost": "26.06"  // 仅仅是展示用
            },
            {
                "main_specification": "蓝色",
                "second_specification": "38",
                "image_url": "https://www.baidu.com1",
                "purchasing_cost": "24.00",
                "original_cost": "34.86",
                "after_discount_cost": "27.19"
            },
            {
                "main_specification": "蓝色",
                "second_specification": "39",
                "image_url": "https://www.baidu.com1",
                "purchasing_cost": "21.00",
                "original_cost": "30.51",
                "after_discount_cost": "23.79"
            },
            {
                "main_specification": "绿色",
                "second_specification": "37",
                "purchasing_cost": "23.00",
                "original_cost": "33.41",
                "after_discount_cost": "26.06"
            },
            {
                "main_specification": "绿色",
                "second_specification": "42",
                "image_url": "https://www.baidu.com",
                "purchasing_cost": "21.00",
                "original_cost": "30.51",
                "after_discount_cost": "23.79"
            }
        ],
        "pics": [
            {
                "main_specification": "蓝色",
                "image_url": "https://www.baidu.com1"
            },
            {
                "main_specification": "绿色",
                "image_url": "https://www.baidu.com"
            }
        ]
    }
}
```

