# 中国官方放假调休数据

经正式通知人工核验的公共年度日历数据，仅包含放假调休日期、版本及官方来源。不包含应用源码、个人日程或用户数据。

固定版本清单：[manifest.json](https://yfuwei.github.io/personal-assistant-calendar-data/manifest.json)。年度数据：[2026-v1.json](https://yfuwei.github.io/personal-assistant-calendar-data/years/2026-v1.json)。

## 已发布年度

2026，`cn-2026-v1` / revision 1：通知明确列明33天放假、6天调休上班。依据《国务院办公厅关于2026年部分节假日安排的通知》，国办发明电〔2025〕7号，成文2025-11-04。

[完整官方转载](https://www.beijing.gov.cn/zhengce/zhengcefagui/202511/t20251104_4258873.html) · [国新办转载](https://www.scio.gov.cn/zdgz/jj/202511/t20251110_938367.html)。普通周末不自动标休；调休仅对应通知同段假期，不猜测具体交换日。当前未发布2027年数据。

## 格式及更新约定

- manifest：`format=personal-assistant.cn-holidays.manifest`、`formatVersion=1`、UTC `publishedAt`与`years`；每年含year/revision/version/path/sha256/bytes。年度路径固定为`years/YYYY-vN.json`，SHA-256和字节数对应发布文件的完整UTF-8原始字节。
- 年度JSON：`format=personal-assistant.cn-holidays`、`formatVersion=1`、publishedAt/yearCount/packs。每包含year、递增revision、`version=cn-YYYY-vN`、complete=true、官方通知source、放假区间holidays与关联workdays、展开后的restDays/workDays计数。
- 同年修订必须升revision；已发布版本文件保持不变，manifest指向最新有效版本。全年七节日完整覆盖；官方合并假期用顿号连接名称，元旦可跨上一年12月。真实日期/数量/重复冲突、官方来源、manifest与数据版本及摘要都须检查。
- 客户端自动检查只读manifest，用户主动刷新才下载年度文件。数据失败/断网时保留内置或有效本机缓存，不运行远程代码。

## 年度维护流程与边界

目前由维护者**人工启动**新年度通知核验：核对正式通知全文、七假期区间和同段补班关系，验证日期/计数、版本及SHA-256，再审核公开文件白名单并发布。新闻标题或未经人工审核的网页解析结果不能直接发布数据。

尚未部署官方通知自动监测、定期抓取、后台服务或自动发布工作流。未确认稳定的官方机器可读年度通知源，因此当前不以不稳定抓取代替人工审核。公开静态JSON更新与上游通知发现是两个独立环节。
