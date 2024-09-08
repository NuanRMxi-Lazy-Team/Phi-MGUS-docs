# GetData

action: `getData`  
所有客户端连接到服务器都会收到此消息，消息带有 `needPassword` 字段，此字段为 `true` 代表服务器设置了密码，密码需要随[ClientMetaData](/Action/Client/ClientMetaData.md)返回，若鉴权失败将返回[JoinServerFailed]()消息并附带原因；字段为 `false` 代表服务器为公开服务器，无需返回密码。若无其他错误将会返回 [JoinServerSuccess]() 消息代表服务器已将客户端加入用户列表。  
更多细节见 [ClientMetaData](/Action/Client/ClientMetaData.md)