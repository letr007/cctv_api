# 获取节目列表信息

> https://api.cntv.cn/NewVideo/getVideoListByColumn?id=TOPC1451559180488841&n=20&sort=desc&p=1&mode=0&serviceId=tvcctv

**请求参数**

*请求方式:GET*


|字段  |类型 |备注 |
|-----|-----|-----|
|id   |str  |id,全站通用唯一标识|
|n    |num  |返回的节目数量|
|sort |str  |暂不明确，可有可无|
|p    |num  |页数。与n字段配合，p*n|
|mode |num  |返回模式。取值[0-2]|
|serviceId|str|[tvcctv]|

需要设置请求头，否则返回
```JSON
{"errcode":"1105","msg":"无效服务"}
```

- 关于mode:

mode字段可取值[0-2],代表三种返回数据格式

mode取值不同返回的data:total及data:list字段有所不同

当mode取值0时返回节目简略数据

当mode取值1时返回节目详细数据

当mode取值2时返回节目简略+详细数据

当mode取值超出范围返回如下:
```json
{
    "errcode": "1001",
    "msg": "url error"
}
```

**JSON回复**

根字段:

|字段 |类型 |内容 |备注 |
|-----|-----|-----|-----|
|data |obj  |信息本体|   |

`data`字段:

|字段 |类型|内容|备注|
|----|----|----|----|
|total|num|(?) |    |
|list|obj |信息列表| |

`data`中的`list`对象:

注意:`list`对象为一个列表,其内包含一个字典,信息如下

|字段 |类型|内容                |备注                    |
|----|----|--------------------|-----------------------|
|guid|str |等于pid，节目唯一标识|不同于上面的id           |
|id  |str |暂未明确是啥id      |跟上面的也不同            |
|time|str |节目发布(首播)时间  |                         |
|title|str|节目标题            |显示在央视网详情界面的标题 |
|length|str|节目总时长         |                         |
|image|str|一个图片链接        |显示在央视网详情界面的预览图|
|focus_date|num|暂未明确       |                         |
|brief|str|节目简介            |                         |
|url |str |节目播放节目的链接   |就是央视网视频播放界面     |
|mode|num |请求模式            |                         |

**示例:**

以《新闻周刊》为例:

**mode=0:**

```shell
curl -H "User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36 Edg/125.0.0.0" -G -d "id=TOPC1451559180488841" -d "n=5" -d "sort=desc" -d "p=1" -d "mode=0" -d "serviceId=tvcctv" https://api.cntv.cn/NewVideo/getVideoListByColumn? | jq
```
<details>
<summary>查看响应示例：</summary>

```JSON
{
    "data": {
        "total": 701,
        "list": [
            {
                "guid": "14b6d6aee34745f292f6fd44ecec5725",
                "id": "VIDERRRY2LKdMa1cnSOCdHHm240601",
                "time": "2024-06-01 22:15:00",
                "title": "《新闻周刊》 20240601",
                "length": "00:43:24",
                "image": "https://p1.img.cctvpic.com/fmspic/2024/06/01/14b6d6aee34745f292f6fd44ecec5725-1.jpg",
                "focus_date": 1717255968610,
                "brief": "本期节目主要内容：\r\n1.本周视点 体育新考；\r\n2.人物回顾；\r\n3.本周人物 王元卓：给孩子的科普；\r\n4.本周特写 雨口夺粮。\r\n（《新闻周刊》 20240601）",
                "url": "https://tv.cctv.com/2024/06/01/VIDERRRY2LKdMa1cnSOCdHHm240601.shtml",
                "mode": 0
            },
            {
                "guid": "44018d94df904dfe83dc76efe41995f2",
                "id": "VIDEFarHMDFVzlRliIIyEcYd240527",
                "time": "2024-05-25 22:10:00",
                "title": "《新闻周刊》 20240525",
                "length": "00:43:04",
                "image": "https://p4.img.cctvpic.com/fmspic/2024/05/27/44018d94df904dfe83dc76efe41995f2-1.jpg",
                "focus_date": 1716745959397,
                "brief": "本期节目主要内容：\r\n1.本周视点 一体化的长三角；\r\n2.人物回顾；\r\n3.本周人物 苏红星：“问诊”田地间；\r\n4.本周特写 回归的“鲸”。\r\n（《新闻周刊》 20240525）",
                "url": "https://tv.cctv.com/2024/05/27/VIDEFarHMDFVzlRliIIyEcYd240527.shtml",
                "mode": 0
            },
            {
                "guid": "8537c9d1d2384fc1a84b003688f03384",
                "id": "VIDE28uNurjkkttTxvUWNjsY240518",
                "time": "2024-05-18 22:15:00",
                "title": "《新闻周刊》 20240518",
                "length": "00:40:49",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/05/18/8537c9d1d2384fc1a84b003688f03384-1.jpg",
                "focus_date": 1716047665201,
                "brief": "本期节目主要内容：\r\n1.本周视点 电池“消”隐患；\r\n2.人物回顾；\r\n3.本周人物 许小猛：“打工”歌手；\r\n4.本周特写 无障碍观影厅。\r\n（《新闻周刊》 20240518）",
                "url": "https://tv.cctv.com/2024/05/18/VIDE28uNurjkkttTxvUWNjsY240518.shtml",
                "mode": 0
            },
            {
                "guid": "aedb7bdaefae4ef583ea024a97aa8a80",
                "id": "VIDEorCIskRQsyNc5K1Z1u1w240511",
                "time": "2024-05-11 22:20:00",
                "title": "《新闻周刊》 20240511",
                "length": "00:43:38",
                "image": "https://p4.img.cctvpic.com/fmspic/2024/05/11/aedb7bdaefae4ef583ea024a97aa8a80-1.jpg",
                "focus_date": 1715441054221,
                "brief": "本期节目主要内容：\r\n1.本周视点 就医“便与利”；\r\n2.人物回顾；\r\n3.本周人物 张晓圆：北大“减肥课”；\r\n4.本周特写 湖中捞物。\r\n（《新闻周刊》 20240511）",
                "url": "https://tv.cctv.com/2024/05/11/VIDEorCIskRQsyNc5K1Z1u1w240511.shtml",
                "mode": 0
            },
            {
                "guid": "bc2a66804ce54189a4c247525d61e071",
                "id": "VIDE1E5jpagnSLNrC2TpqwOx240506",
                "time": "2024-04-27 22:15:00",
                "title": "《新闻周刊》 20240427",
                "length": "00:40:46",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/05/06/bc2a66804ce54189a4c247525d61e071-1.jpg",
                "focus_date": 1714232826394,
                "brief": "本期节目主要内容：\r\n1.本周视点 免疫“谋”规划；\r\n2.人物回顾；\r\n3.本周人物 王印：“水火箭”之梦；\r\n4.本周特写 “救”在洪水中。\r\n（《新闻周刊》 20240427）",
                "url": "https://tv.cctv.com/2024/05/06/VIDE1E5jpagnSLNrC2TpqwOx240506.shtml",
                "mode": 0
            }
        ]
    }
}
```
</details>

**mode=1:**

```shell
curl -H "User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36 Edg/125.0.0.0" -G -d "id=TOPC1451559180488841" -d "n=5" -d "sort=desc" -d "p=1" -d "mode=1" -d "serviceId=tvcctv" https://api.cntv.cn/NewVideo/getVideoListByColumn? | jq
```
<details>
<summary>查看响应示例：</summary>

```JSON
{
    "data": {
        "total": 1000,
        "list": [
            {
                "guid": "4d98d7b16cec411c978b44721c95725b",
                "id": "VIDE6PM4juMlPFfbvXXzfrhO240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周特写 雨口夺粮",
                "length": "00:04:48",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/06/01/4d98d7b16cec411c978b44721c95725b-1.jpg",
                "focus_date": 1717254528458,
                "brief": "在产粮大省河南，夏收工作展开，农户连夜赶收，挑灯夜战，争取雨水天前能完工，当地还协调了省外的农机跨区域作业。",
                "url": "https://tv.cctv.com/2024/06/01/VIDE6PM4juMlPFfbvXXzfrhO240601.shtml",
                "mode": 1
            },
            {
                "guid": "51e494ced11e4724ad81c8fd0bffae64",
                "id": "VIDEeoMogRWE5qP4hisuutVy240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周人物 王元卓：给孩子的科普",
                "length": "00:08:49",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/06/01/51e494ced11e4724ad81c8fd0bffae64-1.jpg",
                "focus_date": 1717254168192,
                "brief": "中国科学院计算技术研究所研究员、中国科普作家协会副理事长王元卓致力于大数据和智能计算等相关工作，作为专业人士，他选择面向公众做科普。",
                "url": "https://tv.cctv.com/2024/06/01/VIDEeoMogRWE5qP4hisuutVy240601.shtml",
                "mode": 1
            },
            {
                "guid": "34e6e4b19e7f45e2a72531eb1b9814e1",
                "id": "VIDENUY5m0XrJHxUoInnC67Z240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]人物回顾",
                "length": "00:03:10",
                "image": "https://p5.img.cctvpic.com/fmspic/2024/06/01/34e6e4b19e7f45e2a72531eb1b9814e1-1.jpg",
                "focus_date": 1717253808587,
                "brief": "人物回顾：\r\n1.竹内亮：真实地纪录；\r\n2.武大靖：任职教授；\r\n3.马中骐：“10001”号博士。",
                "url": "https://tv.cctv.com/2024/06/01/VIDENUY5m0XrJHxUoInnC67Z240601.shtml",
                "mode": 1
            },
            {
                "guid": "3ffcae2ff5a14e79a58d8b59401282ee",
                "id": "VIDE5RSyqGfKbHIGwMfCl2K8240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周视点 体育新考",
                "length": "00:23:13",
                "image": "https://p5.img.cctvpic.com/fmspic/2024/06/01/3ffcae2ff5a14e79a58d8b59401282ee-1.jpg",
                "focus_date": 1717253568532,
                "brief": "记者在现场看到北京、沈阳等地参加体育中考的考生紧张感都有所降低，主要因为这些地方的中考体育评分标准进行了调整，达到良好就满分。",
                "url": "https://tv.cctv.com/2024/06/01/VIDE5RSyqGfKbHIGwMfCl2K8240601.shtml",
                "mode": 1
            },
            {
                "guid": "6c835f02fc6848d6a8f95694e853a494",
                "id": "VIDE09bXgu7zyFALrW84WkNG240527",
                "time": "2024-05-25 22:10:00",
                "title": "[新闻周刊]本周人物 苏红星：“问诊”田地间",
                "length": "00:08:15",
                "image": "https://p4.img.cctvpic.com/fmspic/2024/05/27/6c835f02fc6848d6a8f95694e853a494-1.jpg",
                "focus_date": 1716745118764,
                "brief": "苏红星现在已经67岁，20年前，他从部队转业，承包了一片果园，想自己尝试种出安全健康的农产品。由此这个从没拿过锄头的门外汉，推开了农业种植的门。",
                "url": "https://tv.cctv.com/2024/05/27/VIDE09bXgu7zyFALrW84WkNG240527.shtml",
                "mode": 1
            }
        ]
    }
}
```
</details>

**mode=2:**

```shell
curl -H "User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36 Edg/125.0.0.0" -G -d "id=TOPC1451559180488841" -d "n=5" -d "sort=desc" -d "p=1" -d "mode=2" -d "serviceId=tvcctv" https://api.cntv.cn/NewVideo/getVideoListByColumn? | jq
```
<details>
<summary>查看响应示例：</summary>

```JSON
{
    "data": {
        "total": 1000,
        "list": [
            {
                "guid": "14b6d6aee34745f292f6fd44ecec5725",
                "id": "VIDERRRY2LKdMa1cnSOCdHHm240601",
                "time": "2024-06-01 22:15:00",
                "title": "《新闻周刊》 20240601",
                "length": "00:43:24",
                "image": "https://p1.img.cctvpic.com/fmspic/2024/06/01/14b6d6aee34745f292f6fd44ecec5725-1.jpg",
                "focus_date": 1717255968610,
                "brief": "本期节目主要内容：\r\n1.本周视点 体育新考；\r\n2.人物回顾；\r\n3.本周人物 王元卓：给孩子的科普；\r\n4.本周特写 雨口夺粮。\r\n（《新闻周刊》 20240601）",
                "url": "https://tv.cctv.com/2024/06/01/VIDERRRY2LKdMa1cnSOCdHHm240601.shtml",
                "mode": 0
            },
            {
                "guid": "4d98d7b16cec411c978b44721c95725b",
                "id": "VIDE6PM4juMlPFfbvXXzfrhO240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周特写 雨口夺粮",
                "length": "00:04:48",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/06/01/4d98d7b16cec411c978b44721c95725b-1.jpg",
                "focus_date": 1717254528458,
                "brief": "在产粮大省河南，夏收工作展开，农户连夜赶收，挑灯夜战，争取雨水天前能完工，当地还协调了省外的农机跨区域作业。",
                "url": "https://tv.cctv.com/2024/06/01/VIDE6PM4juMlPFfbvXXzfrhO240601.shtml",
                "mode": 1
            },
            {
                "guid": "51e494ced11e4724ad81c8fd0bffae64",
                "id": "VIDEeoMogRWE5qP4hisuutVy240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周人物 王元卓：给孩子的科普",
                "length": "00:08:49",
                "image": "https://p2.img.cctvpic.com/fmspic/2024/06/01/51e494ced11e4724ad81c8fd0bffae64-1.jpg",
                "focus_date": 1717254168192,
                "brief": "中国科学院计算技术研究所研究员、中国科普作家协会副理事长王元卓致力于大数据和智能计算等相关工作，作为专业人士，他选择面向公众做科普。",
                "url": "https://tv.cctv.com/2024/06/01/VIDEeoMogRWE5qP4hisuutVy240601.shtml",
                "mode": 1
            },
            {
                "guid": "34e6e4b19e7f45e2a72531eb1b9814e1",
                "id": "VIDENUY5m0XrJHxUoInnC67Z240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]人物回顾",
                "length": "00:03:10",
                "image": "https://p5.img.cctvpic.com/fmspic/2024/06/01/34e6e4b19e7f45e2a72531eb1b9814e1-1.jpg",
                "focus_date": 1717253808587,
                "brief": "人物回顾：\r\n1.竹内亮：真实地纪录；\r\n2.武大靖：任职教授；\r\n3.马中骐：“10001”号博士。",
                "url": "https://tv.cctv.com/2024/06/01/VIDENUY5m0XrJHxUoInnC67Z240601.shtml",
                "mode": 1
            },
            {
                "guid": "3ffcae2ff5a14e79a58d8b59401282ee",
                "id": "VIDE5RSyqGfKbHIGwMfCl2K8240601",
                "time": "2024-06-01 22:15:00",
                "title": "[新闻周刊]本周视点 体育新考",
                "length": "00:23:13",
                "image": "https://p5.img.cctvpic.com/fmspic/2024/06/01/3ffcae2ff5a14e79a58d8b59401282ee-1.jpg",
                "focus_date": 1717253568532,
                "brief": "记者在现场看到北京、沈阳等地参加体育中考的考生紧张感都有所降低，主要因为这些地方的中考体育评分标准进行了调整，达到良好就满分。",
                "url": "https://tv.cctv.com/2024/06/01/VIDE5RSyqGfKbHIGwMfCl2K8240601.shtml",
                "mode": 1
            }
        ]
    }
}
```
</details>
