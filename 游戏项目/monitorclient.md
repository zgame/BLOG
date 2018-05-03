# 命令列表

	enum eMDM_LOG
	{
		MDM_LOG = 1100,		//主命令
	};
	
	enum ELOG_SUB				//副命令
	{
		LOGSUB_C_MONITOR_REG = 10,				// 监控客户端注册
		LOGSUB_C_SERVER_REG = 11,				// 服务器注册
		LOGSUB_S_SERVER_REG = 12,				// 服务器注册
	
		LOGSUB_S_MONITOR_ITEMS = 100,			// 下发服务器列表
		LOGSUB_S_MONITOR_STATE = 101,			// 更新状态
		LOGSUB_S_MONITOR_LOG = 103,				// 添加日志
		LOGSUB_S_NEW_MONITOR_ITEM = 104,		// 新增服务器
		LOGSUB_S_DEL_MONITOR_ITEM = 105,		// 服务器断开
	
		LOGSUB_C_MONITOR_KEEPLIVE = 200,		// 心跳包
		LOGSUB_S_MONITOR_KEEPLIVE = 201,		// 心跳包
	
		LOGSUB_C_MONITOR_CMD = 2050,			// 执行命令
		LOGSUB_S_MONITOR_CMD = 2051,			// 执行命令结果
	};

	每次发消息都带标识MAIN_CMD_ID， 这个是主命令
	m_pTcpSession->SendData(MAIN_CMD_ID, nSubMsgId, nullptr, 0);	//#define MAIN_CMD_ID 1100



# 包结构
		
		wMainCmd = wSubCmd = 0;  // 主副命令
		wDataLen = 0; //数据长度
		pDataBuf     //发送的protocol buffer数据

		注意TCPHead，包头




# 流程


1. 连接时候发消息到日志服务器，注册成为客户端

		void ClientSession::OnConnect()
		{
			DebugString(L"OnConnect Success, %s:%d", m_sRemoteIp, m_nRemotePort);
			SendData(SUB_C_MONITOR_REG);		//SUB_C_MONITOR_REG = 10,	// 注册为客户端
		}




2. Update（）的时候 ，开线程接受数据包

		void TcpSession::DealRecvData()
		{
			char* pBuf = m_rcvBuffer;
			WORD wPacketLen = 0;
			while (m_iDataLen >= sizeof(TCPHead))
			{
				TCPHead* pHead = (TCPHead*)pBuf;
				wPacketLen = pHead->TCPInfo.wPacketSize;
				if (sizeof(TCPHead) + wPacketLen > m_iDataLen){
					break;
				}
		
				ASSERT(m_pSink);
				if (m_pSink != nullptr){
					m_pSink->OnDataArrive(pHead->CommandInfo.wMainCmdID, pHead->CommandInfo.wSubCmdID, pBuf+sizeof(TCPHead), wPacketLen);
				}
				
				m_iDataLen = m_iDataLen - sizeof(TCPHead) - wPacketLen;
				pBuf = pBuf + sizeof(TCPHead) + wPacketLen;
			}
		
			if (pBuf != m_rcvBuffer){
				memmove(m_rcvBuffer, pBuf, m_iDataLen);
			}
		}

	
3. ClientSession::OnDataArrive转到MessageHandler的HandlePacket来处理包

4. Update（）的时候 ，发心跳包

		SendData(SUB_C_MONITOR_KEEPLIVE);	//SUB_C_MONITOR_KEEPLIVE = 200 心跳包





















