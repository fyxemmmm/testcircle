## **后台api**
<a href="./#后台api" style="height:50px;width:35px;position:fixed;bottom:100px;right:0px;background:#00BCC1;opacity:0.6;color:#333;text-decoration:none;">回到顶部</a>
- [加盟宝](./#加盟宝)
    - [banner图一套restful](./#banner图一套restful)  

- [规格](./#规格)
    - [规格添加](./#规格添加)  
    - [规格更新](./#规格更新)  
    - [规格详情](./#规格详情)  


## 加盟宝  

### banner图一套restful
- 请求方式: `get`
- 请求地址: `jmb-banners`
- 请求参数:  
restful 风格一套   
- 响应内容:  
```json
{
    "code": 1,
    "message": "success",
    "info": {
        "items": [
            {
                "id": 1,
                "image_url": "https://sshua.oss-cn-shanghai.aliyuncs.com/product/images/timg%20%285%29.jpg",
                "type": 1,
                "jmb_id": 1,
                "use_out_link": 0,
                "out_link_url": ""
            },
            {
                "id": 2,
                "image_url": "https://sshua.oss-cn-shanghai.aliyuncs.com/product/images/timg%20%285%29.jpg",
                "type": 1,
                "jmb_id": 0,
                "use_out_link": 1,
                "out_link_url": "https://www.baidu.com"
            },
            {
                "id": 3,
                "image_url": "https://sshua.oss-cn-shanghai.aliyuncs.com/product/images/timg%20%285%29.jpg",
                "type": 1,
                "jmb_id": 2,
                "use_out_link": 0,
                "out_link_url": ""
            },
            {
                "id": 4,
                "image_url": "https://sshua.oss-cn-shanghai.aliyuncs.com/product/images/timg%20%285%29.jpg",
                "type": 1,
                "jmb_id": 3,
                "use_out_link": 0,
                "out_link_url": ""
            }
        ],
        "_links": {
            "self": {
                "href": "http://my_xijin_service.com/jmb-banners?page=1"
            }
        },
        "_meta": {
            "totalCount": 4,
            "pageCount": 1,
            "currentPage": 1,
            "perPage": 20
        }
    }
}
use_out_link : 如果是1 那么就使用外部链接out_link_url
是0 ：点击图片跳转jmb_id对应详情
use_out_link可以做个√ x之类的啥的吧
```




## 规格  
### 规格添加
- 请求方式: `post`
- 请求地址: `goods-specifications`
- 请求参数:  
```json
{
	"goods_id": 1,
	"main_specification_name": "颜色",
	"second_specification_name": "鞋码",
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
			"second_specification": "38",
			"purchasing_cost": 22
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

