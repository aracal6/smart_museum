# 智能博物馆PRD文档（百度api）
## 价值主张设计

#### 加值宣言
- 随着教育水平的提高，文化水平的上升，越来越多的人喜欢游览博物馆去了解历史了解艺术文化。博物馆的数量越来越多，场馆也越来越大。在博物馆满足人们精神文化消费的同时，也面临着许多问题。随着游客的增多，博物馆的人手开始出现不足的情况，展品的介绍栏虽然详细，但是客流量多的时候将会给游客带来不好的体验。同时，博物馆越做越大，许多第一次来的游客会不知道从何“游”起的迷惘。所以基于博物馆目前存在的导览情况，本项目将结合人工智能api来解决导览难的问题，保障游客的游览体验感。

优先级：运用语音合成api，为游客提供图文并茂的介绍，减轻工作人员的负担，提高游客观览体验感。
次优先级：运用地标功能，拍下周围的环境，识别当前位置，导航游客去往目的地并规划游览路线。


#### 核心价值
本产品着力于提升游客的游览体验，解决用户游览时遇到的无介绍，不识路，无目的的游览迷惘问题。


#### 核心价值与用户痛点
- 便捷性：不用询问工作人员，直接打开手机APP，便有图文并茂的展品介绍。引导游客去往目的，规划好路线，减少不必要的时间浪费
- 收益性：能够减少博物馆的人力成本支出

#### 需求列表与人工智能API加值
|  用户需求   |   重要性  |    api技术接口 |
| --- | --- | --- |
|  用户想要面前展品的信息、介绍   |   重要  | 语音合成  |
|  用户想想去某个展区  |  重要   | 地标识别    |

具体使用场景：
- 小明周日来到博物馆，由于周日放假的原因，游客特别多，他找不到有空的工作人员来给他介绍面前的展品，他打开博物馆导览app，搜索展品，app弹出关于该产品所有的信息介绍，还有语音播报方便小明边看边听。

- 小明第一次来到这个博物馆，由于博物馆很大，他找到了路标指引还是没有找到目的地，这时，他打开app，拍下路标，app给他实时导航路线并规划好游览的路线。
## 产品设计原型
#### 产品架构图
![b175824709eda5cd027b1e160e5e551.png](https://upload-images.jianshu.io/upload_images/9643258-d341e30bfed04789.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 交互及界面设计
![79bd812bb29d35dba12ee5fdfe48df3.png](https://upload-images.jianshu.io/upload_images/9643258-4947c8fff3be17a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## API 产品使用及输出展示
- 语音合成api
- 接口描述：
- 接口调用：
```
result  = client.synthesis('你好百度', 'zh', 1, {
    'vol': 5,
})

# 识别正确返回语音二进制 错误则返回dict 参照下面错误码
if not isinstance(result, dict):
    with open('auido.mp3', 'wb') as f:
        f.write(result)
```

- 输出：
```
// 成功返回二进制文件流
// 失败返回
{
    "err_no":500,
    "err_msg":"notsupport.",
    "sn":"abcdefgh",
    "idx":1
}
```

![2322dc151b65a4c355b7e614069f204.png](https://upload-images.jianshu.io/upload_images/9643258-cf1e8642369d0d6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



- 地标识别api
- 接口描述：该请求用于识别地标，即对于输入的一张图片（可正常解码，且长宽比适宜），输出图片中的地标识别结果。
- 接口调用：
```
# encoding:utf-8

import requests
import base64

'''
地标识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/landmark"
# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img}
access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```

- 输出
```
{"log_id": 3450013152046070669, "result": {"landmark": "狮身人面像"}}
```


