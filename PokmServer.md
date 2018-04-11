*************************************************************************************************
MainServer:-----------游戏逻辑服务器

apps/common/middlewares/auth.py	----用户认证中间件，包括一些渠道认证
apps/common/rkauth.py(game_auth.py)----生成认证的cookie
apps/common/sequence.py		----sql数据库中最新的uid
apps/common/sequence_union.py	----sql数据库中最新的联盟uid
apps/config/cache.conf		----memcache的配置
apps/config/game_config.py	----策划填写配置表的结构定义，加载配置表reload_game_config，更新配置表数据
apps/config/model.conf		----memcache数据库中各个表结构
apps/config/storage.conf	----存储的配置文件
apps/config/system_config.py	----作废
apps/game_config/		----新的结构里面定义:策划填写的配置表具体数据
apps/logics/*			----游戏逻辑处理部分，是所有跟客户端的接口，接口里面调用logic里面的具体操作, 然后把结果返回给客户端
apps/logics/activity_logic/*	----活动部分逻辑
apps/logics/band_logic/*	----组合的逻辑
apps/logics/battle/*		----竞技场战斗，通用战斗，跨服战斗，经验，金币，道馆，三大，四大，关卡，夺宝，试练，精华试练，联盟3v3，联盟关卡，世界boss等战斗逻辑
apps/logics/battle_ship_logic/*	----战舰战斗的逻辑
apps/logics/buddy_logic/*	----好友的逻辑
apps/logics/catch_monster_logic/*----抓宠逻辑
apps/logics/chat_logic/*	----聊天的逻辑
apps/logics/chest_logic/*	----开宝箱的逻辑
apps/logics/cross_server_arena_logic/*----跨服战的逻辑
apps/logics/daily_task_logic/*	----每日任务的逻辑
apps/logics/draw_logic/*	----单抽的逻辑
apps/logics/exchange_code_logic/*----兑换码的逻辑
apps/logics/fishing_logic/*	----钓鱼的逻辑
apps/logics/fragment_shop_logic/*----碎片商店的逻辑
apps/logics/gift_logic/*	----礼包的逻辑
apps/logics/gym_logic/*		----道馆的逻辑和道馆商店的逻辑
apps/logics/item_logic/*	----道具的逻辑
apps/logics/item_packet_drop_logic/*----掉落包的逻辑
apps/logics/king_arena_logic/*	----三大的逻辑
apps/logics/master_arena_logic/*----四大的逻辑
apps/logics/login_7_logic/*	----7天登录的逻辑
apps/logics/massage_logic/*	----按摩的逻辑
apps/logics/notice_logic/*	----广播的逻辑
apps/logics/plate_shop_logic/*	----mega商店的逻辑
apps/logics/player_arena_logic/*----竞技场的逻辑
apps/logics/player_invitation_logic/*----玩家邀请
apps/logics/player_logic/*	----每日充值，满额充值，新手引导，玩家逻辑
apps/logics/player_reward_seven_level_logic/*----开服7天等级逻辑
apps/logics/player_reward_seven_power_logic/*----开服7天战力逻辑
apps/logics/pvp_shop_logic/*	----竞技场商店的逻辑
apps/logics/recharge_return_logic/*----充值返还活动的逻辑
apps/logics/reward/*		----成就宝藏的逻辑
apps/logics/server_quiz_logic/*	----问答的逻辑
apps/logics/server_world_boss_logic/*----世界boss和世界boss商店的逻辑
apps/logics/player_sign_30_logic/*----三大的逻辑
apps/logics/stage_logic/*	----金币本，经验本，普通本的关卡逻辑
apps/logics/stone_shop_logic/*	----钻石商城的逻辑
apps/logics/treasure_logic/*	----夺宝的逻辑
apps/logics/trial_essense_logic/*----熔炼精华的逻辑
apps/logics/trial_logic/*	----试练的逻辑
apps/logics/union_3v3_logic/*	----联盟3v3的逻辑
apps/logics/union_logic/*	----联盟聊天，联盟，联盟商店
apps/logics/vip_reward_logic/*	----vip每日奖励的逻辑
apps/logics/weapon_logic/*	----装备强化的逻辑
apps/logics/zone_logic/*	----区域的逻辑
apps/logs/action/		----所有自身log记录的具体执行文件
apps/logs/output_action.py	----log函数的列表文件,是所有log具体操作的接口文件
apps/models/*			----游戏数据处理部分
apps/models/activity/*		----活动部分的数据模型和简单操作，update_dat刷新数据，add_activities_num
apps/models/base/*		----大部分基础的数据结构，数据结构定义，初始化init，install，reset
apps/models/buddy/*		----好友部分
apps/models/common/*		----获取共有部分，包含聊天，排行榜，三大，四大，关卡排行,世界boss，配置文件，广播，提交bug，玩家好友，玩家昵称，各种活动，服务器数据，按照等级进行玩家分类，问答，关卡，系统邮件，联盟名字
apps/models/cross_battle/*	----玩家跨服数据
apps/models/gym/*		----玩家的道馆数据，玩家道馆商店，道馆排行
apps/models/mail/*		----玩家邮箱，玩家私信
apps/models/mysql/*		----活动列表，管理员登录log，万能兑换码，礼包类型，具体兑换码，玩家充值记录，兑换码兑换
apps/models/player_world_boss/*	----世界boss鼓舞，挑战次数等，2个boss类再分别继承，玩家的世界boss商店
apps/models/recharge_return/*	----充值返还
apps/models/slate/*		----石板
apps/models/thread_action/*	----更新联盟搜索，好友搜索，联盟等级排行，联盟关卡排行，玩家通信，竞技场，三大，四大，道馆，关卡排行，玩家升级带来的等级变动
apps/models/treasure/*		----玩家夺宝数据，玩家拥有的宝物，服务器掌握的夺宝列表
apps/models/union/*		----联盟数据，联盟聊天，联盟等级排行，联盟搜索，联盟商城，联盟关卡，联盟关卡排行，联盟成员数据
apps/models/union_3v3/*		----联盟3v3数据
apps/models/account_mapping.py	----账号映射
apps/models/daily_recharge_reward.py----每日充值的数据
apps/models/daily_task.py	----每日任务
apps/models/daily_vip_reward.py	----每日vip奖励
apps/models/ditto_shop.py	----百变怪商城
apps/models/gift_bag.py		----礼包
apps/models/hand_book.py	----图鉴
apps/models/items.py		----道具
apps/models/monster.py		----怪物
apps/models/monster_equip.py	----怪物装备
apps/models/name_mapping.py	----名字映射
apps/models/player.py		----玩家数据
apps/models/player_arena_battle_report.py----战报系统
apps/models/player_arena_honour.py----竞技场荣誉
apps/models/player_catch_monster.py----抓宠
apps/models/player_fragment_shop.py----碎片商城
apps/models/player_invitation.py----玩家邀请好友加入游戏
apps/models/player_king_arena_battle_report.py----三大战报
apps/models/player_master_arena_battle_report.py----四大战报
apps/models/player_login_7.py	----七天登录
apps/models/player_payment.py	----玩家充值数据
apps/models/player_plate_shop.py----三大、四大商城
apps/models/player_pvp_shop.py	----竞技场商城
apps/models/player_quiz.py	----问答
apps/models/player_random_state.py----随机数
apps/models/player_reward_seven_level.py----开服7天冲级
apps/models/player_reward_seven_power.py----开服7天战力
apps/models/player_sign_30.py	----30天签到
apps/models/player_stone_shop.py----钻石商城
apps/models/player_team.py	----玩家队伍
apps/models/player_team_band.py	----小伙伴
apps/models/player_trial_battle.py----试练
apps/models/player_trial_essence.py----精华试练
apps/models/stage.py		----关卡
apps/models/sum_recharge_reward.py----每日充值
apps/models/user.py		----玩家
apps/models/zone.py		----区域数据
apps/models/user_king_arena.py	----三大
apps/models/user_master_arena.py----四大
apps/platform/platform.py	----加载平台配置的信息
../../platform/platform.conf	----数据库等配置的key，memcache和sql的服务器地址，密码，server id等配置
apps/server_thread/script/*	----刷新公有数据的脚本
apps/server_thread/script/buddy/*----重新生成玩家好友搜索，刷新用户通讯部分
apps/server_thread/script/gym/*	----刷新道馆排名
apps/server_thread/script/server_player_level_distribution/*----刷新玩家等级分组
apps/server_thread/script/stage/*----刷新关卡排行
apps/server_thread/script/treasure/*----刷新宝物分布
apps/server_thread/script/union/*----刷新联盟等级，成员，搜索，联盟关卡
apps/settings/*			----定义几个conf的路径
apps/utils/_init_.py		----工具函数（区间随机，权重随机，memcache get，memcache put，查list，逗号分隔的互相转换)
apps/utils/battle_define.py	----战斗中使用的常量定义
apps/utils/encryption.py	----聊天加密
apps/utils/game_define.py	----游戏常量定义
apps/utils/model_define.py	----定义memcache的存储路径,后面有一些新修改的增加了服务器的区分
apps/utils/mysql_conncection.py	----定义mysql的存储路径定义
apps/utils/payment_util.py	----定义支付验签
apps/utils/server_define.py	----定义原来的合服映射
apps/utils/server_util.py	----获取用户ip地址
apps/utils/user_ip_time_limit_check.py----限制玩家发消息过于频繁
apps/views/game_config.py	----策划配置表的GM后台的配置及配置表的更新
apps/views/main.py		----index登录回调接口，api接口，chat聊天获取接口的逻辑实现
apps/views/platform.py		----来自serverlist的支付回调，判断增加钻石ok后回传serverlist告知ok，支付成功之后会记录到mysql里面player_charge_rmb
apps/game_nginx.conf		----游戏服务器的配置
apps/game_server_thread.py	----游戏服务器的自动启动线程,包括（更新服务器活动状态；还有一些共有数据的更新）
apps/game_server_thread_model_reset.py----作废
apps/game_wsgi.ini		----wsgi的配置表
apps/manage.py			----wsgi初始化的时候会调用，初始化
apps/urls.py			----游戏回调接口，包括平台支付接口，配置更新和更新时间修改，获取聊天信息接口，index登录接口，api接口
logs/				----以后的日志会打印到这个目录下面，比如game_error，wsgi的log等
rklib/				----基础库，也有平台的支付验证的库文件
scribe/				----日志收集，将每天的日志打印出来，供后期分析和记录用
script/				----独立运行的脚本，用来处理一些合服、刷排行榜等信息的处理
script/backup_cmem/*		----memcache的备份脚本
script/clear_user/*		----删掉共有数据，个人数据，邀请等玩家信息
script/cross_server/*		----重新计算关卡的排行，更新玩家战斗力
script/log/*			----分析日志响应时间
script/merge_server/*		----合服，合并共有数据
script/open_server/*		----开服脚本
script/user/*			----玩家脚本
script/user/arena/*		----刷新竞技场排行
script/user/buddy/*		----清除好友中不存在的用户
script/user/gym/*		----重置玩家道馆数据
script/user/recharge/*		----给玩家充值指定金额
script/user/stage/*		----重置精英副本数据
script/user/treasure/*		----清除夺宝数据
script/user/union/*		----联盟改名，修复奖励
statistics/			----打印日志相关
*************************************************************************************************
GameManager（GameLogServer）:-----------游戏GM后台和日志服务器
apps/game_manager/models
apps/game_manager/mysql/mysql_connect----sql数据库连接，后台的sql数据库放在每个游戏对应数据库中，包括后台登信息
apps/game_manager/mysql/*	----后台进行数据库操作时候的具体sql语句和逻辑，这里要特别注意game_id是定义了后台所写死的游戏编号1.皮卡丘2.战舰3.xyz4.待定
apps/game_manager/templates	----前端网页的html模板
apps/game_manager/views		----网页调用的逻辑执行python代码，处理好的数据返回给templates里面的网页
apps/game_manager/game_manage_define.py----定义权限和页面
apps/game_manager/urls.py	----页面回调跳转地址的定义，GM后台的html跳转
apps/logs/*			----日志的记录逻辑，以前有很多日志的记录点
apps/game_manager/views/server/version_notice.py----公告逻辑操作
apps/game_manager/mysql/server_notice.py----公告操作的数据库操作,从sql进行操作
apps/game_manager/views/gm/get_chat_content.py----获取聊天信息
apps/utils/server_define.py	----定义memcache的服务器存储
apps/utils/model_define.py	----定义memcache的存储路径定义
apps/game_manager/util/memcache.py----定义memchache的存储和读取
apps/game_manager/util/mysql_util.py----定义mysql的存储,里面有不少查询sql数据库记录的用户总体记录情况
apps/logs/statistics_tables/product_daily_situation/statistics_total.py----总体统计的逻辑，用的mysql查询数据
apps/game_manager/views/server/client_config.py----上传配置文件
apps/game_manager/views/server/server_config.py----修改服务器版本号，更新服务器配置生效(配置文件同步到游戏服务器)，更新客户端配置时间(强制玩家同步)，通过http协议通知游戏服务器这些消息

日志服务器启动和关闭方法（日志和gm后台也是一个游戏一个）
日志服 皮卡丘是用的8083端口，开启关闭用start_uwsgi.sh stop_uwsgi.sh
战舰是8084端口，开启是start84.sh，关闭是先sudo netstat -ntlp查看8084端口的进程号，用kill命令直接杀掉进程。8085 8086 8087也是一样

*************************************************************************************************
GameServerList:-----------服务器列表（跟bundle共用一个服务器）
apps/urls.py			----页面回调跳转地址的定义，登录和支付
apps/views/server_list.py	----查找皮卡丘的数据库serverlist表，这里有所有游戏的服务器列表
apps/utils/mysql_connection.py	----连接mysql服务器
apps/utils/server_notice.py	----查找服务器公告，这里要便利所有的表了，因为数据保存在各个游戏自己的数据库中
apps/utils/payment_util.py	----支付验签的逻辑
apps/views/platform.py		----各个渠道平台的登录和支付验证逻辑代码
apps/views/account.py		----apple store自己的登录系统
apps/utils/user_list.py		----apple store自研登录系统的获取用户等函数


登录流程：
客户端发请求->serverlist->渠道登录，根据渠道返回参数整理（timeout=10）->serverlist验证后回调->客户端
支付流程：
客户端发请求->渠道支付，渠道支付完成回调->serverlist,支付通知->gameserver加钻石->加成功返回serverlist成功->返回渠道通知成功->渠道返回客户端


serverlist启动和关闭方法（其中涉及多个游戏的服务器列表）
只有皮卡丘目录下面的是有用的，数据库中也是皮卡丘的serverlist有用
serverlist开启关闭是start_uwsgi.sh stop_uwsgi.sh

*************************************************************************************************
SQL数据库部分：

MySQL(log_server)		----按照每天的情况记录日志，每个游戏一个库，每个库一天一个表记录当天每一个登录的玩家信息，等级，按照日期，id，设备id，uid，ip，月卡，连续登陆时间
MySQL（game_manager）		----每个游戏有一个库，每个库有一系列表
activity_list	----后台控制的各个充值等活动的开启控制
admin_log	----记录管理员登录
admin_manager	----管理员表
all_exchange_code----固定的新手礼包
all_gift_package----推广礼包，永久礼包，固定输入的
cross_server	----跨服战的后台设置
cross_server_rank----跨服战的发奖
exchange_code	----所有兑换码和对应的礼包码
gift_package	----礼包码编号
mail		----空
player_charge_rmb----用户的充值表
sequence	----玩家最新uid序列
sequence_union	----联盟最新uid序列
server_list	----server list 服务器列表,只有皮卡丘下面是有用的，皮卡丘的表serverlist保存所有游戏的服务器数据
server_merge_mapping----服务器映射表
server_notice	----服务器公告
union_battle_3v3----3v3联盟战配置
union_battle_3v3_rank----3v3联盟战的排行

*************************************************************************************************
CrossServer:-----------游戏跨服PK服务器
apps/logics/			----游戏跨服逻辑部分
跨服另外用一个memcache，称为共有数据
apps/utils/server_define.py	----服务器的定义，服务器映射在游戏的mysql数据库中有server_merge_mapping表
apps/utils/union_3v3.py		----通过mysql获取联盟战的一些配置数据
apps/common/common_dat.py	----游戏服务器部分存储调用方法，获得各种分组数据，排行榜等
apps/models/*			----数据模块的定义，都是类的形式定义的，里面也有成员函数
apps/script/send_union_3v3_mail.py----3v3结束之后发奖的逻辑，调用model的mail添加操作，然后保存

*************************************************************************************************
GameLogParse:-----------日志解析逻辑
将日志服务器打印出来的日志文件进行解析，然后保存到对应的小文件中，方便日后读取

*************************************************************************************************
pycharm设置：
project: Project Interpreter:Django,pip,setuptools,simplejson,xlrd


*************************************************************************************************
mem_engine_obj = app.get_engine("mem").client
common_dat.py
game_config_version_model.py
player_nick_name.py
union_name.py



-------------------------------gm后台修改权限------------------------------------------------------------
apps/game_manager/urls.py 地址到python代码的映射

apps/game_manager/game_manage_define.py定义了所有的权限，包括地址是否可以访问；VIEW_BUTTON是按钮（左侧列表）是否可以显示
apps/game_manager/templates/base/base.html定义了所有界面的跳转地址，是否现实和开启