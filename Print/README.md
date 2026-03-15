graph LR
    A[HP M451dn 印表機] -- SNMP 協定 --> B(Zabbix Server)
    B -- 數據存儲 --> C{Zabbix DB}
    D[Grafana] -- Zabbix Plugin --> B
    D -- JSON 配置渲染 --> E[6F/7F 印表機監控面板]
    
    subgraph 監控指標
    F(剩餘碳粉 %)
    G(總列印頁數)
    H(設備即時狀態)
    end
    B --> F
    B --> H
    B --> G