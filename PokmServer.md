*************************************************************************************************
MainServer:-----------��Ϸ�߼�������

apps/common/middlewares/auth.py	----�û���֤�м��������һЩ������֤
apps/common/rkauth.py(game_auth.py)----������֤��cookie
apps/common/sequence.py		----sql���ݿ������µ�uid
apps/common/sequence_union.py	----sql���ݿ������µ�����uid
apps/config/cache.conf		----memcache������
apps/config/game_config.py	----�߻���д���ñ�Ľṹ���壬�������ñ�reload_game_config���������ñ�����
apps/config/model.conf		----memcache���ݿ��и�����ṹ
apps/config/storage.conf	----�洢�������ļ�
apps/config/system_config.py	----����
apps/game_config/		----�µĽṹ���涨��:�߻���д�����ñ��������
apps/logics/*			----��Ϸ�߼������֣������и��ͻ��˵Ľӿڣ��ӿ��������logic����ľ������, Ȼ��ѽ�����ظ��ͻ���
apps/logics/activity_logic/*	----������߼�
apps/logics/band_logic/*	----��ϵ��߼�
apps/logics/battle/*		----������ս����ͨ��ս�������ս�������飬��ң����ݣ������Ĵ󣬹ؿ����ᱦ����������������������3v3�����˹ؿ�������boss��ս���߼�
apps/logics/battle_ship_logic/*	----ս��ս�����߼�
apps/logics/buddy_logic/*	----���ѵ��߼�
apps/logics/catch_monster_logic/*----ץ���߼�
apps/logics/chat_logic/*	----������߼�
apps/logics/chest_logic/*	----��������߼�
apps/logics/cross_server_arena_logic/*----���ս���߼�
apps/logics/daily_task_logic/*	----ÿ��������߼�
apps/logics/draw_logic/*	----������߼�
apps/logics/exchange_code_logic/*----�һ�����߼�
apps/logics/fishing_logic/*	----������߼�
apps/logics/fragment_shop_logic/*----��Ƭ�̵���߼�
apps/logics/gift_logic/*	----������߼�
apps/logics/gym_logic/*		----���ݵ��߼��͵����̵���߼�
apps/logics/item_logic/*	----���ߵ��߼�
apps/logics/item_packet_drop_logic/*----��������߼�
apps/logics/king_arena_logic/*	----������߼�
apps/logics/master_arena_logic/*----�Ĵ���߼�
apps/logics/login_7_logic/*	----7���¼���߼�
apps/logics/massage_logic/*	----��Ħ���߼�
apps/logics/notice_logic/*	----�㲥���߼�
apps/logics/plate_shop_logic/*	----mega�̵���߼�
apps/logics/player_arena_logic/*----���������߼�
apps/logics/player_invitation_logic/*----�������
apps/logics/player_logic/*	----ÿ�ճ�ֵ�������ֵ����������������߼�
apps/logics/player_reward_seven_level_logic/*----����7��ȼ��߼�
apps/logics/player_reward_seven_power_logic/*----����7��ս���߼�
apps/logics/pvp_shop_logic/*	----�������̵���߼�
apps/logics/recharge_return_logic/*----��ֵ��������߼�
apps/logics/reward/*		----�ɾͱ��ص��߼�
apps/logics/server_quiz_logic/*	----�ʴ���߼�
apps/logics/server_world_boss_logic/*----����boss������boss�̵���߼�
apps/logics/player_sign_30_logic/*----������߼�
apps/logics/stage_logic/*	----��ұ������鱾����ͨ���Ĺؿ��߼�
apps/logics/stone_shop_logic/*	----��ʯ�̳ǵ��߼�
apps/logics/treasure_logic/*	----�ᱦ���߼�
apps/logics/trial_essense_logic/*----�����������߼�
apps/logics/trial_logic/*	----�������߼�
apps/logics/union_3v3_logic/*	----����3v3���߼�
apps/logics/union_logic/*	----�������죬���ˣ������̵�
apps/logics/vip_reward_logic/*	----vipÿ�ս������߼�
apps/logics/weapon_logic/*	----װ��ǿ�����߼�
apps/logics/zone_logic/*	----������߼�
apps/logs/action/		----��������log��¼�ľ���ִ���ļ�
apps/logs/output_action.py	----log�������б��ļ�,������log��������Ľӿ��ļ�
apps/models/*			----��Ϸ���ݴ�����
apps/models/activity/*		----����ֵ�����ģ�ͺͼ򵥲�����update_datˢ�����ݣ�add_activities_num
apps/models/base/*		----�󲿷ֻ��������ݽṹ�����ݽṹ���壬��ʼ��init��install��reset
apps/models/buddy/*		----���Ѳ���
apps/models/common/*		----��ȡ���в��֣��������죬���а������Ĵ󣬹ؿ�����,����boss�������ļ����㲥���ύbug����Һ��ѣ�����ǳƣ����ֻ�����������ݣ����յȼ�������ҷ��࣬�ʴ𣬹ؿ���ϵͳ�ʼ�����������
apps/models/cross_battle/*	----��ҿ������
apps/models/gym/*		----��ҵĵ������ݣ���ҵ����̵꣬��������
apps/models/mail/*		----������䣬���˽��
apps/models/mysql/*		----��б�����Ա��¼log�����ܶһ��룬������ͣ�����һ��룬��ҳ�ֵ��¼���һ���һ�
apps/models/player_world_boss/*	----����boss���裬��ս�����ȣ�2��boss���ٷֱ�̳У���ҵ�����boss�̵�
apps/models/recharge_return/*	----��ֵ����
apps/models/slate/*		----ʯ��
apps/models/thread_action/*	----���������������������������˵ȼ����У����˹ؿ����У����ͨ�ţ��������������Ĵ󣬵��ݣ��ؿ����У�������������ĵȼ��䶯
apps/models/treasure/*		----��Ҷᱦ���ݣ����ӵ�еı�����������յĶᱦ�б�
apps/models/union/*		----�������ݣ��������죬���˵ȼ����У����������������̳ǣ����˹ؿ������˹ؿ����У����˳�Ա����
apps/models/union_3v3/*		----����3v3����
apps/models/account_mapping.py	----�˺�ӳ��
apps/models/daily_recharge_reward.py----ÿ�ճ�ֵ������
apps/models/daily_task.py	----ÿ������
apps/models/daily_vip_reward.py	----ÿ��vip����
apps/models/ditto_shop.py	----�ٱ���̳�
apps/models/gift_bag.py		----���
apps/models/hand_book.py	----ͼ��
apps/models/items.py		----����
apps/models/monster.py		----����
apps/models/monster_equip.py	----����װ��
apps/models/name_mapping.py	----����ӳ��
apps/models/player.py		----�������
apps/models/player_arena_battle_report.py----ս��ϵͳ
apps/models/player_arena_honour.py----����������
apps/models/player_catch_monster.py----ץ��
apps/models/player_fragment_shop.py----��Ƭ�̳�
apps/models/player_invitation.py----���������Ѽ�����Ϸ
apps/models/player_king_arena_battle_report.py----����ս��
apps/models/player_master_arena_battle_report.py----�Ĵ�ս��
apps/models/player_login_7.py	----�����¼
apps/models/player_payment.py	----��ҳ�ֵ����
apps/models/player_plate_shop.py----�����Ĵ��̳�
apps/models/player_pvp_shop.py	----�������̳�
apps/models/player_quiz.py	----�ʴ�
apps/models/player_random_state.py----�����
apps/models/player_reward_seven_level.py----����7��弶
apps/models/player_reward_seven_power.py----����7��ս��
apps/models/player_sign_30.py	----30��ǩ��
apps/models/player_stone_shop.py----��ʯ�̳�
apps/models/player_team.py	----��Ҷ���
apps/models/player_team_band.py	----С���
apps/models/player_trial_battle.py----����
apps/models/player_trial_essence.py----��������
apps/models/stage.py		----�ؿ�
apps/models/sum_recharge_reward.py----ÿ�ճ�ֵ
apps/models/user.py		----���
apps/models/zone.py		----��������
apps/models/user_king_arena.py	----����
apps/models/user_master_arena.py----�Ĵ�
apps/platform/platform.py	----����ƽ̨���õ���Ϣ
../../platform/platform.conf	----���ݿ�����õ�key��memcache��sql�ķ�������ַ�����룬server id������
apps/server_thread/script/*	----ˢ�¹������ݵĽű�
apps/server_thread/script/buddy/*----����������Һ���������ˢ���û�ͨѶ����
apps/server_thread/script/gym/*	----ˢ�µ�������
apps/server_thread/script/server_player_level_distribution/*----ˢ����ҵȼ�����
apps/server_thread/script/stage/*----ˢ�¹ؿ�����
apps/server_thread/script/treasure/*----ˢ�±���ֲ�
apps/server_thread/script/union/*----ˢ�����˵ȼ�����Ա�����������˹ؿ�
apps/settings/*			----���弸��conf��·��
apps/utils/_init_.py		----���ߺ��������������Ȩ�������memcache get��memcache put����list�����ŷָ��Ļ���ת��)
apps/utils/battle_define.py	----ս����ʹ�õĳ�������
apps/utils/encryption.py	----�������
apps/utils/game_define.py	----��Ϸ��������
apps/utils/model_define.py	----����memcache�Ĵ洢·��,������һЩ���޸ĵ������˷�����������
apps/utils/mysql_conncection.py	----����mysql�Ĵ洢·������
apps/utils/payment_util.py	----����֧����ǩ
apps/utils/server_define.py	----����ԭ���ĺϷ�ӳ��
apps/utils/server_util.py	----��ȡ�û�ip��ַ
apps/utils/user_ip_time_limit_check.py----������ҷ���Ϣ����Ƶ��
apps/views/game_config.py	----�߻����ñ��GM��̨�����ü����ñ�ĸ���
apps/views/main.py		----index��¼�ص��ӿڣ�api�ӿڣ�chat�����ȡ�ӿڵ��߼�ʵ��
apps/views/platform.py		----����serverlist��֧���ص����ж�������ʯok��ش�serverlist��֪ok��֧���ɹ�֮����¼��mysql����player_charge_rmb
apps/game_nginx.conf		----��Ϸ������������
apps/game_server_thread.py	----��Ϸ���������Զ������߳�,���������·������״̬������һЩ�������ݵĸ��£�
apps/game_server_thread_model_reset.py----����
apps/game_wsgi.ini		----wsgi�����ñ�
apps/manage.py			----wsgi��ʼ����ʱ�����ã���ʼ��
apps/urls.py			----��Ϸ�ص��ӿڣ�����ƽ̨֧���ӿڣ����ø��º͸���ʱ���޸ģ���ȡ������Ϣ�ӿڣ�index��¼�ӿڣ�api�ӿ�
logs/				----�Ժ����־���ӡ�����Ŀ¼���棬����game_error��wsgi��log��
rklib/				----�����⣬Ҳ��ƽ̨��֧����֤�Ŀ��ļ�
scribe/				----��־�ռ�����ÿ�����־��ӡ�����������ڷ����ͼ�¼��
script/				----�������еĽű�����������һЩ�Ϸ���ˢ���а����Ϣ�Ĵ���
script/backup_cmem/*		----memcache�ı��ݽű�
script/clear_user/*		----ɾ���������ݣ��������ݣ�����������Ϣ
script/cross_server/*		----���¼���ؿ������У��������ս����
script/log/*			----������־��Ӧʱ��
script/merge_server/*		----�Ϸ����ϲ���������
script/open_server/*		----�����ű�
script/user/*			----��ҽű�
script/user/arena/*		----ˢ�¾���������
script/user/buddy/*		----��������в����ڵ��û�
script/user/gym/*		----������ҵ�������
script/user/recharge/*		----����ҳ�ֵָ�����
script/user/stage/*		----���þ�Ӣ��������
script/user/treasure/*		----����ᱦ����
script/user/union/*		----���˸������޸�����
statistics/			----��ӡ��־���
*************************************************************************************************
GameManager��GameLogServer��:-----------��ϷGM��̨����־������
apps/game_manager/models
apps/game_manager/mysql/mysql_connect----sql���ݿ����ӣ���̨��sql���ݿ����ÿ����Ϸ��Ӧ���ݿ��У�������̨����Ϣ
apps/game_manager/mysql/*	----��̨�������ݿ����ʱ��ľ���sql�����߼�������Ҫ�ر�ע��game_id�Ƕ����˺�̨��д������Ϸ���1.Ƥ����2.ս��3.xyz4.����
apps/game_manager/templates	----ǰ����ҳ��htmlģ��
apps/game_manager/views		----��ҳ���õ��߼�ִ��python���룬����õ����ݷ��ظ�templates�������ҳ
apps/game_manager/game_manage_define.py----����Ȩ�޺�ҳ��
apps/game_manager/urls.py	----ҳ��ص���ת��ַ�Ķ��壬GM��̨��html��ת
apps/logs/*			----��־�ļ�¼�߼�����ǰ�кܶ���־�ļ�¼��
apps/game_manager/views/server/version_notice.py----�����߼�����
apps/game_manager/mysql/server_notice.py----������������ݿ����,��sql���в���
apps/game_manager/views/gm/get_chat_content.py----��ȡ������Ϣ
apps/utils/server_define.py	----����memcache�ķ������洢
apps/utils/model_define.py	----����memcache�Ĵ洢·������
apps/game_manager/util/memcache.py----����memchache�Ĵ洢�Ͷ�ȡ
apps/game_manager/util/mysql_util.py----����mysql�Ĵ洢,�����в��ٲ�ѯsql���ݿ��¼���û������¼���
apps/logs/statistics_tables/product_daily_situation/statistics_total.py----����ͳ�Ƶ��߼����õ�mysql��ѯ����
apps/game_manager/views/server/client_config.py----�ϴ������ļ�
apps/game_manager/views/server/server_config.py----�޸ķ������汾�ţ����·�����������Ч(�����ļ�ͬ������Ϸ������)�����¿ͻ�������ʱ��(ǿ�����ͬ��)��ͨ��httpЭ��֪ͨ��Ϸ��������Щ��Ϣ

��־�����������͹رշ�������־��gm��̨Ҳ��һ����Ϸһ����
��־�� Ƥ�������õ�8083�˿ڣ������ر���start_uwsgi.sh stop_uwsgi.sh
ս����8084�˿ڣ�������start84.sh���ر�����sudo netstat -ntlp�鿴8084�˿ڵĽ��̺ţ���kill����ֱ��ɱ�����̡�8085 8086 8087Ҳ��һ��

*************************************************************************************************
GameServerList:-----------�������б���bundle����һ����������
apps/urls.py			----ҳ��ص���ת��ַ�Ķ��壬��¼��֧��
apps/views/server_list.py	----����Ƥ��������ݿ�serverlist��������������Ϸ�ķ������б�
apps/utils/mysql_connection.py	----����mysql������
apps/utils/server_notice.py	----���ҷ��������棬����Ҫ�������еı��ˣ���Ϊ���ݱ����ڸ�����Ϸ�Լ������ݿ���
apps/utils/payment_util.py	----֧����ǩ���߼�
apps/views/platform.py		----��������ƽ̨�ĵ�¼��֧����֤�߼�����
apps/views/account.py		----apple store�Լ��ĵ�¼ϵͳ
apps/utils/user_list.py		----apple store���е�¼ϵͳ�Ļ�ȡ�û��Ⱥ���


��¼���̣�
�ͻ��˷�����->serverlist->������¼�������������ز�������timeout=10��->serverlist��֤��ص�->�ͻ���
֧�����̣�
�ͻ��˷�����->����֧��������֧����ɻص�->serverlist,֧��֪ͨ->gameserver����ʯ->�ӳɹ�����serverlist�ɹ�->��������֪ͨ�ɹ�->�������ؿͻ���


serverlist�����͹رշ����������漰�����Ϸ�ķ������б�
ֻ��Ƥ����Ŀ¼����������õģ����ݿ���Ҳ��Ƥ�����serverlist����
serverlist�����ر���start_uwsgi.sh stop_uwsgi.sh

*************************************************************************************************
SQL���ݿⲿ�֣�

MySQL(log_server)		----����ÿ��������¼��־��ÿ����Ϸһ���⣬ÿ����һ��һ�����¼����ÿһ����¼�������Ϣ���ȼ����������ڣ�id���豸id��uid��ip���¿���������½ʱ��
MySQL��game_manager��		----ÿ����Ϸ��һ���⣬ÿ������һϵ�б�
activity_list	----��̨���Ƶĸ�����ֵ�Ȼ�Ŀ�������
admin_log	----��¼����Ա��¼
admin_manager	----����Ա��
all_exchange_code----�̶����������
all_gift_package----�ƹ����������������̶������
cross_server	----���ս�ĺ�̨����
cross_server_rank----���ս�ķ���
exchange_code	----���жһ���Ͷ�Ӧ�������
gift_package	----�������
mail		----��
player_charge_rmb----�û��ĳ�ֵ��
sequence	----�������uid����
sequence_union	----��������uid����
server_list	----server list �������б�,ֻ��Ƥ�������������õģ�Ƥ����ı�serverlist����������Ϸ�ķ���������
server_merge_mapping----������ӳ���
server_notice	----����������
union_battle_3v3----3v3����ս����
union_battle_3v3_rank----3v3����ս������

*************************************************************************************************
CrossServer:-----------��Ϸ���PK������
apps/logics/			----��Ϸ����߼�����
���������һ��memcache����Ϊ��������
apps/utils/server_define.py	----�������Ķ��壬������ӳ������Ϸ��mysql���ݿ�����server_merge_mapping��
apps/utils/union_3v3.py		----ͨ��mysql��ȡ����ս��һЩ��������
apps/common/common_dat.py	----��Ϸ���������ִ洢���÷�������ø��ַ������ݣ����а��
apps/models/*			----����ģ��Ķ��壬���������ʽ����ģ�����Ҳ�г�Ա����
apps/script/send_union_3v3_mail.py----3v3����֮�󷢽����߼�������model��mail��Ӳ�����Ȼ�󱣴�

*************************************************************************************************
GameLogParse:-----------��־�����߼�
����־��������ӡ��������־�ļ����н�����Ȼ�󱣴浽��Ӧ��С�ļ��У������պ��ȡ

*************************************************************************************************
pycharm���ã�
project: Project Interpreter:Django,pip,setuptools,simplejson,xlrd


*************************************************************************************************
mem_engine_obj = app.get_engine("mem").client
common_dat.py
game_config_version_model.py
player_nick_name.py
union_name.py



-------------------------------gm��̨�޸�Ȩ��------------------------------------------------------------
apps/game_manager/urls.py ��ַ��python�����ӳ��

apps/game_manager/game_manage_define.py���������е�Ȩ�ޣ�������ַ�Ƿ���Է��ʣ�VIEW_BUTTON�ǰ�ť������б��Ƿ������ʾ
apps/game_manager/templates/base/base.html���������н������ת��ַ���Ƿ���ʵ�Ϳ���