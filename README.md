# 智能博物馆PRD文档（百度api）
## 一、使用者需求概述
- 目标用户：博物馆相关的工作人员

- 功能使用场景描述

（1）博物馆的馆藏展品需要被借出或者进行维修时，工作人员来到展品柜台的防盗智能锁，进行人脸识别打开展品柜台取出展品。

（2）博物馆的管理人员双手拿着东西无法用手开门，通过人脸对比识别出工作人员，并且把门打开。

## 二、产品主要概述总结
#### 功能
- 通过使用百度平台提供的人脸搜索API和人脸识别API，连接到博物馆展品柜台的防盗系统，防盗系统对需要开启柜台锁的工作人员进行脸部搜索并进行人脸识别。识别通过， “滴”声后成功开锁；未通过者则提示需再次识别，两次未通过者可进行第三次人脸识别，但此时的识别人数需增加至两个，两个皆成功通过后方可开锁；第三次仍未成功，防盗系统自动发出“防盗”警告。
- 工作人员上传证件照及其身份证，通过识别照片上的人像，快速确认其是否有相应的权限。并且，需要两人或是三人同时认证成功，权限才会开放，即博物馆的展品柜打开。门认证成功后可以根据表情或是其他指令控制门的开启与关闭，保护安全性的同时，也使展品的运输更为方便，节省时间。

#### 整合功能
- 博物馆工作人员可以在特定的小程序中完成个人资料（基本信息、面部信息等）录入，审核通过后可在小程序中查看自己负责的藏品信息。（藏品所有负责人姓名及工号、藏品储藏位置、藏品编号、收入库时间）。当需要取出藏品时提前在小程序中提交申请，审核通过后刷脸即可取出。

## 三、成本效益分析
#### 成本

1.人脸识别系统的功耗大于普通锁头、指纹锁等传统设备，且需连续运作，产生一定耗电量。

2.要保证在紧急情况下能应对停电、无网络等状况，要配备机械方式以供紧急开关。

3.要配合证件信息（内置芯片、条形码等）双重认证进一步增强安全性。
 
#### 效益

1.不需要与人体产生直接的接触，就能使用摄像机获取人脸图像。增加效率，解放工作人员的双手，尤其在手持馆品或其他物件的时候。

2.安全性能高。人脸识别系统的识别程度很高，他人无法轻易模仿。

3.技术识别证件和人像，鉴别持工作证为本人，确保“人证合一”。

## 四、产品原型流程图

![输入图片说明](https://images.gitee.com/uploads/images/2019/1112/210950_544b24c0_1922226.png "产品原型.png")
