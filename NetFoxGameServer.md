# 网狐引擎，满贯捕鱼服务器代码结构

（缺点：功能代码目录分的不好，大量代码写到一起去，看着乱，难维护）

---

# 登录服务器

AttemperEngineSink.cpp

	连接中心服，上报玩家状态，数量
	连接日志服务器
	工会通知，登录处理
	列表处理OnTCPNetworkMainPCServerList，包含获取列表，获取房间，获取在线
	服务处理，包含账号密码修改，金币充值转账等
	游戏列表OnBPCGameListResult
	各种活动奖励，签到
	升级炮座，合成，分解道具  


DataBaseEngineSink.cpp	//数据库的操作

	登录，注册账号，游客登录，游客账号绑定，修改头像，修改密码
	加载游戏列表OnRequestLoadGameList
	登录成功OnLogonDisposeResult
	加载各种奖励，公告
	竞技场，排行榜，大奖赛，用户幸运数字

PlayerSession.cpp

	兑换灵力，兑换弹头，保存钻币，保存鱼卷，记录玩家物品变更

ServerListManager.cpp

	插入，删除房间，



# 中心服务器

AttemperEngineSink.cpp

	登录验证，玩家信息查询，发送到游戏服务器，加载竞技场活动配置

BossSkill.cpp
	
	boss技能

ClassicPrizePool.cpp

	累计奖池， 轮盘抽奖

DBRecordSink.cpp

	数据库保存， 世界boss记录，奖池记录，梦幻排行记录


# 游戏服务器

Analyze.cpp

	玩家金币的变化，开火，打到鱼的检测

AttemperEngineSink.cpp
	
	发送消息给协调服，日志监控服
	玩家升级， 解锁炮
	用户抽奖， 钻石， 奖券， 等级，
	用户坐下， 聊天， 表情， 私聊
	踢出用户，踢出所有用户，
	道具效果，产生红包，抢红包
	群发数据
	机器人炮倍数
	创建桌子， 创建公会桌子
	用户任务， 活跃度奖励， 

TableFrame.cpp

	桌子的操作， 写入钻石，积分，写入一大堆信息

# 协调服务器

AttemperEngineSink.cpp
	
	发送服务器列表， 发消息给游戏服务器


# 捕鱼游戏

（竞技场，逻辑都差不多，代码copy的）

AIGameLogic.cpp

	机器人自动瞄准

FishManager.cpp

	鱼类的生成，获取，更新

FishManager_form.cpp

	生成鱼的各种阵



# 白名单和维护逻辑

	游戏服务器OnEventControl,控制事件
	CT_CONTROL_SAVE_SERVER被通知游戏服务器维护
	CServerRule::SetForfendGameEnter(m_pGameServiceOption->llServerRule, true);  //设置不能进入

	CT_LOAD_SERVICE_CONFIG被通知加载配置，并关闭维护状态

	白名单的判断有问题，一共5个地方要改（游戏服务器的OnTCPNetworkSubLogonUserID, 登录服务器的DoSDKLogin,OnTCPNetworkSubMBGuessLogin,OnTCPNetworkSubMBRegisterAccounts,OnTCPNetworkSubMBLogonAccounts）



	