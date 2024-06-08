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
|column_brief |str |空的 o_o    |           |
|column_photo |str |栏目图片链接 |似乎与column_logo一致?|
|column_firstclass|str|(?)      |           |

