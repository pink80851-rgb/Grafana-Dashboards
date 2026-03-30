UPS 監控專案 (SRE Dashboard)
1. 專案目標

本專案旨在建立一個針對 UPS（不斷電系統）及相關 IT 設備的即時監控與可視化平台，以支持 SRE 團隊：

實時監控 UPS 電池容量、輸入/輸出電壓、負載及可運行時間。
提供警報和性能指標，幫助快速定位潛在故障。
支援擴展至伺服器、網路設備及印表機等監控需求。
2. 技術架構

本專案採用以下技術堆疊：

資料來源 (Data Source):
Zabbix
 作為後端監控資料平台。
可視化 (Visualization):
Grafana
 作為 Dashboard 平台，整合 Zabbix 資料源。
通知與警報 (Alerting):
Grafana Alerts 配合 Zabbix Trigger 監控 UPS 狀態。
部署架構:
Dashboard 前端 → Grafana → Zabbix Server → UPS / 伺服器 / 網路設備。

架構示意圖：

+------------+       +--------+       +---------+
|  UPS / HW  | --->  | Zabbix | --->  | Grafana |
+------------+       +--------+       +---------+
                                   (Dashboard / Alerts)
3. Dashboards 功能概覽
Dashboard 名稱	Panel 名稱	類型	功能描述
UPS-飛瑞	電池容量	Bar Gauge	顯示 UPS 當前電池剩餘容量百分比
UPS-飛瑞	輸出電壓	Stat	顯示 UPS 的輸出電壓 (V)
UPS-飛瑞	可運行時間	Stat	顯示 UPS 在當前負載下的估計運行時間
UPS-飛瑞	電池負載	Gauge	顯示 UPS 負載百分比，警示高負載情況
UPS-飛瑞	輸入電壓	Stat	顯示 UPS 的輸入電壓 (V)
UPS-飛瑞	溫度	Stat	顯示 UPS 溫度 (°C)，超過閾值顯示紅色
Dashboard 連結（Grafana Links）
不斷電系統 (UPS)
6樓伺服器 (PC)
其他狀態 (Other)
印表機 (Printer)
公司網路 (Switch)
4. 擴展性
可新增更多 Zabbix 主機或模板監控，如伺服器、網路設備、印表機等。
Grafana Dashboard 支援插件擴展與自定義 Panel。
警報與通知可整合 Slack、Teams 或 Email。
5. 技術亮點
即時監控：結合 Zabbix 與 Grafana 的時間序列資料，可呈現 UPS 即時狀態。
多維度可視化：使用 Bar Gauge、Gauge、Stat 等不同類型 Panel，呈現多種資訊。
閾值告警：透過 Threshold 設定，自動高亮異常數值。
可擴充與重用：Dashboard 結構模板化，支援多 UPS 與其他設備監控。
SRE 專案導向：專注於可靠性與運維效率，提供運維團隊快速洞察系統健康狀態。
