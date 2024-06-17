# 获取搜索栏目结果

> https://api.cntv.cn/lanmu/columnSearch?&fl=&fc=&cid=&p=2&n=20&serviceId=tvcctv&t=jsonp&cb=Callback

**请求参数**

*请求方式:`GET`*

|字段  |类型 |备注 |
|-----|-----|-----|
|fl   |null |(?)  |
|fc   |null |(?)  |
|cid  |null |(?)  |
|p    |num  |页数  |
|n    |num  |每页显示数量|
|serviceId|str|[tvcctv]|
|t    |str  |[jsonp/json],非必需|
|cb   |str  |[Callback]|

需要设置请求头，否则返回
```JSON
{"errcode":"1105","msg":"无效服务"}
```

- 关于`t`:

`t`可取值json或jsonp,取值json/jsonp仅对部分内容排列顺序有影响

下面给出不同部分:

`t`取值json:
```JSON 
{
    ...
    {
        ...
        "lastVIDE": {
                        "videoUrl": "https:\/\/tv.cctv.com\/2024\/06\/08\/VIDE4sMoEypJlZopDWAb2Xsv240608.shtml",
                        "videoTitle": "\u300a\u65b0\u95fb\u8054\u64ad\u300b 20240608 21:00",
                        "videoId": "VIDE4sMoEypJlZopDWAb2Xsv240608",
                        "videoSharedCode": "989b7afccbde4e67830e869b184b62ee"
                    }
    }
}
```

`t`取值jsonp:
```JSON 
{
    ...
    {
        ...
        "lastVIDE": {
                        "videoUrl": "https:\/\/tv.cctv.com\/2024\/06\/08\/VIDE4sMoEypJlZopDWAb2Xsv240608.shtml",
                        "videoSharedCode": "989b7afccbde4e67830e869b184b62ee",
                        "videoId": "VIDE4sMoEypJlZopDWAb2Xsv240608",
                        "videoTitle": "\u300a\u65b0\u95fb\u8054\u64ad\u300b 20240608 21:00"
                    }
    }
}
```

**JSON回复**

`Callback`:

注：`Callback`不是一个有效的JSON对象，其类似元组( )

|字段 |类型 |内容 |备注 |
|-----|-----|-----|-----|
|response|obj|回复本体|  |

`Callback`中的`response`字段:

|字段 |类型 |内容 |备注 |
|-----|-----|-----|-----|
|docs |obj  |详情数据|   |
|numFound|num|508|      |

`response`中的`docs`字段:

|字段         |类型 |内容       |备注        |
|-------------|----|-----------|-----------|
|column_id    |str |栏目ID     |            |
|column_name  |str |栏目名称    |           |
|channel_name |str |播出频道    |           |
|column_logo  |str |栏目图标链接 |           |
|column_website|str|栏目首页链接 |           |
|column_playdate|str|栏目播出时间|           |
|column_backvideoaddress|str|(?)|与column_website一致|
|column_brief |str |栏目介绍    |           |
|column_photo |str |栏目图片链接 |似乎与column_logo一致?|
|column_firstclass|str|播出频道 |           |
|column_secondclass|str|播出频道|           |
|vms_video_album_id|str|(?)    |            |
|lastVIDE     |obj |(?)        |            |

`docs`中的`lastVIDE`字段:

|字段         |类型 |内容       |备注        |
|-------------|----|-----------|-----------|
|videoUrl     |str |视频播放链接|            |
|videoSharedCode|str|(?)       |            |
|videoId      |str |视频ID     |不知道是什么ID|
|videoTitle   |str |视频标题   |            |

**示例**

```shell
curl -H "User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36 Edg/125.0.0.0" -G -d "fl=" -d "fc=" -d "cid=" -d "p=1" -d "n=3" -d "serviceId=tvcctv" -d "t=jsonp" -d "cb=Callback" https://api.cntv.cn/lanmu/columnSearch?
```

<details>
<summary>查看响应示例：</summary>

返回数据中unicode编码均已转换

```JSON
Callback(
    {
        "response": {
            "docs": [
                {
                    "column_id": "EPGM1387361853673102",
                    "column_name": "新闻联播",
                    "channel_name": "CCTV-1 综合",
                    "column_logo": "https:\/\/p3.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2019\/5\/29\/1559095198581_853.jpg",
                    "column_website": "https:\/\/tv.cctv.com\/lm\/xwlb\/index.shtml",
                    "column_playdate": "每日19:00",
                    "column_backvideoaddress": "https:\/\/tv.cctv.com\/lm\/xwlb\/index.shtml",
                    "column_brief": "",
                    "column_photo": "https:\/\/p5.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2019\/5\/29\/1559095201325_886.jpg",
                    "column_firstclass": "新闻",
                    "column_secondclass": "综合",
                    "vms_video_album_id": "C10437",
                    "lastVIDE": {
                        "videoUrl": "https:\/\/tv.cctv.com\/2024\/06\/17\/VIDEnGBphBzziTzEHkLsOeQr240617.shtml",
                        "videoSharedCode": "fa42814348c24f8aa551213e57202a1f",
                        "videoId": "VIDEnGBphBzziTzEHkLsOeQr240617",
                        "videoTitle": "《新闻联播》 20240617 21:00"
                    }
                },
                {
                    "column_id": "EPGM1387361853673118",
                    "column_name": "焦点访谈",
                    "channel_name": "CCTV-13 新闻",
                    "column_logo": "https:\/\/p1.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2019\/5\/29\/1559095229796_295.jpg",
                    "column_website": "https:\/\/tv.cctv.com\/lm\/jdft\/index.shtml",
                    "column_playdate": "周一至周日19:38",
                    "column_backvideoaddress": "https:\/\/tv.cctv.com\/lm\/jdft\/index.shtml",
                    "column_brief": "《焦点访谈》栏目开办于1994年4月1日，由中央电视台新闻评论部创办，是以深度报道为主、以舆论监督见长的电视新闻评论性栏目。《焦点访谈》的舆论监督节目多年来为人们所关注和喜爱，选择“政府重视、群众关心、普遍存在”的选题，坚持“用事实说话”的方针，反映和推动解决了大量社会进步与发展过程中存在的问题。首播时间：19:38；重播时间：次日03:45，05:45。",
                    "column_photo": "https:\/\/p5.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2019\/5\/29\/1559095232190_675.jpg",
                    "column_firstclass": "新闻",
                    "column_secondclass": "综合",
                    "vms_video_album_id": "C10326",
                    "lastVIDE": {
                        "videoUrl": "https:\/\/tv.cctv.com\/2024\/06\/17\/VIDE7dllJUxXHYLeQMBJN67P240617.shtml",
                        "videoSharedCode": "fd0c7dc2076d475f8918c6ef7cebec8b",
                        "videoId": "VIDE7dllJUxXHYLeQMBJN67P240617",
                        "videoTitle": "《焦点访谈》 20240617 降本增效“公转铁”"
                    }
                },
                {
                    "column_id": "EPGM1718344300730293",
                    "column_name": "健康中国",
                    "channel_name": "CCTV-4 (亚洲)",
                    "column_logo": "https:\/\/p2.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2024\/6\/14\/1718344243324_365.jpg",
                    "column_website": "https:\/\/tv.cctv.com\/lm\/jkzg\/index.shtml",
                    "column_playdate": "周日17:00",
                    "column_backvideoaddress": "https:\/\/tv.cctv.com\/lm\/jkzg\/index.shtml",
                    "column_brief": "《健康中国》栏目由健康中国家、健康中国说、健康中国行、健康中国运动处方四大板块构成，集权威性、前瞻性、服务性、可视性为一体，立足外宣，借健康讲好中国幸福美好生活方式，呈现全身心的大健康理念、全景式的东方生活画卷、全息中国的天地生命诗篇。",
                    "column_photo": "https:\/\/p5.img.cctvpic.com\/photoAlbum\/page\/performance\/img\/2024\/6\/14\/1718344247938_605.jpg",
                    "column_firstclass": "健康",
                    "column_secondclass": "",
                    "vms_video_album_id": "VSET1hdvor73oserhj76aj6tq0",
                    "lastVIDE": {
                        "videoUrl": "https:\/\/tv.cctv.com\/2024\/06\/16\/VIDEMHcIk3rlCjDspbZzgmDA240616.shtml",
                        "videoSharedCode": "7604c1104b1845e08fe8ee9fd4201b67",
                        "videoId": "VIDEMHcIk3rlCjDspbZzgmDA240616",
                        "videoTitle": "《健康中国》 20240616 前列战“腺”不发炎"
                    }
                },
            ],
            "numFound": 509
        }
    }
);
```

</details>

