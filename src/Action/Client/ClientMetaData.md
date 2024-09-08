# ClientMetaData

action: `clientMetaData`  
此消息所有客户端在收到[GetData](/Action/Server/GetData.md)后都需返回，此消息所返回数据应该位于 `data` 字段下，该字段下包含以下字段：

|      字段       |     类型     |    默认值    |                  描述                  | 支持状态 |
|:-------------:|:----------:|:---------:|:------------------------------------:|:----:|
|   features    | JsonObject |     -     |               可选的支持功能                |  ×   |
|  clientName   |   string   | anonymous |              模拟器名称，允许匿名              |  √   |
| clientVersion |    int     |    -1     |           客户端版本号，`-1`代表匿名            |  ×   |
|   userName    |  string?   |   null    |            用户名，`null`代表匿名            |  √   |
|   password    |  string?   |   null    |      密码，服务器为私有时需要本字段，否则为`null`       |  √   |
|  isDebugger   |    bool    |   false   | 是否为调试器，此字段在服务器为调试模式的同时为`true`有效，否则无效 |  ×   |
|  isSpectator  |    bool    |   false   |                是否为旁观者                |  ×   |

其中features字段结构为：

|         字段          |  类型  |  默认值  |                    描述                    | 支持状态 |
|:-------------------:|:----:|:-----:|:----------------------------------------:|:----:|
|   RealTimeUpload    | bool | false |     实时上传，为`true`时客户端需要上传包含每一次点击的所有数据     |  ×   |
|   VotingSelection   | bool | false |          投票选谱，需要全房间人同时支持本功能才可使用          |  ×   |
| RealTimeLeaderboard | bool | false |       实时排行榜，为`true`时服务器将上传其他人的分数数据       |  ×   |
|    RealTimeChat     | bool | false | 实时聊天，为`true`时服务器将上传其他人的聊天信息，同时客户端也需启用本功能 |  ×   |

消息样例：
```json
{
  "features":
  {
    "RealTimeUpload": false,
    "VotingSelection": false,
    "RealTimeLeaderboard": false,
    "RealTimeChat": false
  },
  "clientName": "anonymous",
  "clientVersion": -1,
  "userName": null,
  "password": null,
  "isDebugger": false,
  "isSpectator": false
}

```


# 代码行为
1. 若服务器多次收到此消息，服务器将直接切断连接。
2. 服务器允许用户名重名。