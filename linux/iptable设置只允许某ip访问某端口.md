# iptable设置只允许某ip访问某端口
  step1 ：对整个服务器（全部ip）禁止xxxx端口  
  `iptables -I INPUT -p tcp --dport ${port} -j DROP`  
  step2 ：添加允许的ip  
  `iptables -I INPUT -s ${sourceIp} -p tcp --dport ${port} -j ACCEPT`  
  step3 ：保存设置  
  `service iptables save`  
  step4 ：重启iptables服务  
  `service iptables restart`  
