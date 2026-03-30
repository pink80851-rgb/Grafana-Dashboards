- 監控關鍵 IT 設備，包括：
  - 印表機 (剩餘碳粉、印數量、狀態)
  - UPS / 不斷電系統
  - 伺服器健康狀態
  - 公司網路設備 (Switch)
- 可視化設備狀態，提供即時統計與告警
- 方便運維團隊快速掌握系統健康狀態
- 為 SRE 團隊建立 SLA/SLO 監控基礎

## 技術架構

- **資料來源**：Zabbix SNMP 監控
- **可視化**：Grafana Dashboard
- **資料展示**：
  - Stat Panels：總印數量、印表機狀態
  - BarGauge：碳粉剩餘量百分比
  - Dashboard Links：快速跳轉至 UPS、伺服器、印表機、網路等面板

## 主要功能

| 面板 | 描述 |
|------|------|
| 總印數量 (黑/藍/粉/黃) | 即時顯示各色印表機總印量 |
| 剩餘碳粉 (黑/藍/粉/黃) | 顯示各色碳粉剩餘百分比，紅色警示低於安全值 |
| 印表機狀態 | 顯示印表機即時狀態，支援快速連結到各樓層設備 |
| Dashboard Links | 可快速跳轉到 UPS、伺服器、其他設備監控 |

## 安裝與設定

1. 安裝 Zabbix 代理與 SNMP 監控
2. 將設備加入 Zabbix Host 群組
3. 配置 Grafana Zabbix Datasource
4. 匯入本 JSON Dashboard
5. 根據公司需求修改 `$Print` Host 變數

## 擴展性

- 可擴展至更多設備，例如：
  - 網路交換器監控
  - 伺服器 CPU / Memory / Disk 使用率
- 可結合 Prometheus、Alertmanager 進行自動告警
- 適合 SRE 團隊建立 **SLO / SLA 監控**流程

## 技術亮點

- 結合 SNMP 與 Zabbix 監控，對設備狀態有完整可視化
- Grafana Dashboard 設計，可快速對不同設備分類管理
- 支援即時告警與狀態追蹤，符合 SRE 可觀察性原則
