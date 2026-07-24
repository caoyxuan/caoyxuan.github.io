# Shun Lee 本地标点 10 条自然路线与静态可达性
- 来源: `runtime/shun-lee-review-vnc/20260716_clean_v3_shun_lee_review_vnc/local-user-waypoints/shunlee-marked-waypoints.txt`
- World: `eval/snapshots/imported_1_21_1/shun-lee-clean-v3/world`
- 点数: 39；路线数: 10；primary 覆盖: 39/39
- 说明: `connector` 是为保持路线自然而重复出现的衔接点；覆盖统计只按 `primary` 计一次。
- 边界: 这是静态 world 几何寻路结果，不等于真人/agent 实走通过；`all_segments_certified` 最适合优先人工审核。

## 总览
- 路线状态: {"all_segments_certified": 7, "no_static_route_found": 1, "partial_static_route": 2}
- 路段状态: {"certified_static_reference": 31, "no_path_found": 4}
- 坐标贴近: {"exact_standable": 36, "snapped": 3}
- 非认证/失败路段数: 4

### 需要人工优先确认的路段
- SLR-N03 SLR-N03-S01: 顺利队宿舍3号楼 -> 顺利纪律宿舍2座 (no_path_found)
- SLR-N09 SLR-N09-S01: 教堂3楼暗处 -> 为什么这里卡住了 (no_path_found)
- SLR-N09 SLR-N09-S02: 为什么这里卡住了 -> 教堂4楼暗处 (no_path_found)
- SLR-N10 SLR-N10-S01: 教堂6楼平台入口 -> 需要蹲下的门 (no_path_found)

## SLR-N01 · 住宅塔楼到消防宿舍入口
- 城市类型: high-rise estate spine + estate service entrance
- 场景组合: 住宅塔楼、楼间平台、消防宿舍楼、宿舍区入口
- 操作重点: 住宅楼间连续步行、院区入口识别、平台边界判断
- 人工审核意图: 从楼8沿住宅塔楼群走到消防宿舍区入口，先核对同一高层住区内部动线。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=269.2, turns=46, ascent=0, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 楼8 | primary | -185,10,-619 | -185,10,-619 | 0.0 |
| 2 | via | 楼7 | primary | -196,10,-657 | -196,10,-657 | 0.0 |
| 3 | via | 楼6 | primary | -211,10,-696 | -211,10,-696 | 0.0 |
| 4 | via | 顺利消防宿舍楼5 | primary | -248,10,-673 | -248,10,-673 | 0.0 |
| 5 | end | 顺利消防宿舍区入口 | primary | -267,10,-549 | -267,10,-549 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N01-S01 | 楼8 -> 楼7 | certified_static_reference | 46.2 | 41 | diagonal:15,walk:25 |
| SLR-N01-S02 | 楼7 -> 楼6 | certified_static_reference | 44.8 | 40 | diagonal:14,walk:25 |
| SLR-N01-S03 | 楼6 -> 顺利消防宿舍楼5 | certified_static_reference | 46.9 | 40 | diagonal:19,walk:20 |
| SLR-N01-S04 | 顺利消防宿舍楼5 -> 顺利消防宿舍区入口 | certified_static_reference | 131.3 | 124 | diagonal:20,walk:103 |

## SLR-N02 · 纪律部队宿舍核心院区
- 城市类型: institutional residential estate core
- 场景组合: 宿舍区入口、宿舍楼、操场、院区内部道路
- 操作重点: 院区内部连通、楼栋间定位、操场边界识别
- 人工审核意图: 从消防宿舍区入口进入纪律部队宿舍核心，按院区内部顺序核对楼栋和操场。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=158.5, turns=47, ascent=4, descent=4, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利消防宿舍区入口 | connector | -267,10,-549 | -267,10,-549 | 0.0 |
| 2 | via | 顺利部队宿舍1号楼 | primary | -268,10,-574 | -268,10,-574 | 0.0 |
| 3 | via | 顺利部队操场 | primary | -280,10,-563 | -280,10,-563 | 0.0 |
| 4 | via | 顺利纪律部队2号楼 | primary | -287,10,-618 | -287,10,-618 | 0.0 |
| 5 | end | 顺利队宿舍3号楼 | primary | -300,10,-664 | -300,10,-664 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N02-S01 | 顺利消防宿舍区入口 -> 顺利部队宿舍1号楼 | certified_static_reference | 26.1 | 25 | diagonal:1,step:4,walk:19 |
| SLR-N02-S02 | 顺利部队宿舍1号楼 -> 顺利部队操场 | certified_static_reference | 16.5 | 13 | diagonal:9,step:1,walk:2 |
| SLR-N02-S03 | 顺利部队操场 -> 顺利纪律部队2号楼 | certified_static_reference | 66.0 | 60 | diagonal:15,step:2,walk:42 |
| SLR-N02-S04 | 顺利纪律部队2号楼 -> 顺利队宿舍3号楼 | certified_static_reference | 50.0 | 46 | diagonal:12,walk:33 |

## SLR-N03 · 纪律宿舍坡地远端补点
- 城市类型: estate hillside/peripheral link
- 场景组合: 宿舍核心末端、远端楼座、坡地边缘
- 操作重点: 高差确认、远端楼座定位、断点人工复核
- 人工审核意图: 从已确认的宿舍3号楼继续找远端纪律宿舍2座，单独作为坡地边缘补点路线。
- 静态状态: no_static_route_found；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=, turns=, ascent=, descent=, doors=

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利队宿舍3号楼 | connector | -300,10,-664 | -300,10,-664 | 0.0 |
| 2 | end | 顺利纪律宿舍2座 | primary | -268,2,-744 | -270,2,-741 | 3.6 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N03-S01 | 顺利队宿舍3号楼 -> 顺利纪律宿舍2座 | no_path_found |  |  |  |

## SLR-N04 · 消防交通到足球场环线
- 城市类型: emergency service frontage + sports/transit edge
- 场景组合: 公交站、五人制足球场、足球场侧门/正门、消防局
- 操作重点: 公交边界、场地围栏、门口识别、沿街转向
- 人工审核意图: 从消防公交车站沿运动场边缘走到消防局门口，核对公共设施和球场入口。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=237.0, turns=61, ascent=3, descent=3, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 消防公交车站 | primary | -163,-3,-696 | -163,-3,-696 | 0.0 |
| 2 | via | 顺利邨游乐场五人制足球场 | primary | -137,-1,-694 | -137,-1,-694 | 0.0 |
| 3 | via | 顺足侧门 | primary | -118,-2,-674 | -118,-2,-674 | 0.0 |
| 4 | via | 顺利足球场正门 | primary | -142,-1,-671 | -142,-1,-671 | 0.0 |
| 5 | via | 顺利消防局 | primary | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 6 | end | 顺利消防局门口 | primary | -90,-3,-623 | -90,-3,-623 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N04-S01 | 消防公交车站 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 66.9 | 63 | diagonal:10,step:1,walk:51 |
| SLR-N04-S02 | 顺利邨游乐场五人制足球场 -> 顺足侧门 | certified_static_reference | 27.0 | 21 | diagonal:17,walk:3 |
| SLR-N04-S03 | 顺足侧门 -> 顺利足球场正门 | certified_static_reference | 25.8 | 26 | diagonal:1,step:1,walk:23 |
| SLR-N04-S04 | 顺利足球场正门 -> 顺利消防局 | certified_static_reference | 85.8 | 77 | diagonal:23,walk:53 |
| SLR-N04-S05 | 顺利消防局 -> 顺利消防局门口 | certified_static_reference | 31.4 | 32 | step:1,walk:30 |

## SLR-N05 · 盛德学校到教堂外围设施
- 城市类型: school/civic/religious mixed frontage
- 场景组合: 篮球场、扶幼中心、教堂餐厅、羽毛球场、书院
- 操作重点: 学校周边、庭院/球场边界、建筑入口附近定位
- 人工审核意图: 沿学校和教堂旁的日常设施走一条低层生活线，最后接到迦南书院。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=350.3, turns=76, ascent=10, descent=10, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 盛德学校篮球场 | primary | -206,-2,-550 | -206,-2,-550 | 0.0 |
| 2 | via | 盛德扶幼中心 | primary | -211,-2,-599 | -211,-2,-599 | 0.0 |
| 3 | via | 教堂餐厅 | primary | -107,-2,-596 | -107,-2,-596 | 0.0 |
| 4 | via | 羽毛球场 | primary | -92,-2,-573 | -92,-2,-573 | 0.0 |
| 5 | end | 迦南書院 | primary | -49,-2,-613 | -49,-2,-613 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N05-S01 | 盛德学校篮球场 -> 盛德扶幼中心 | certified_static_reference | 112.6 | 90 | diagonal:57,walk:32 |
| SLR-N05-S02 | 盛德扶幼中心 -> 教堂餐厅 | certified_static_reference | 130.9 | 120 | diagonal:18,step:8,walk:93 |
| SLR-N05-S03 | 教堂餐厅 -> 羽毛球场 | certified_static_reference | 29.0 | 25 | diagonal:12,walk:12 |
| SLR-N05-S04 | 羽毛球场 -> 迦南書院 | certified_static_reference | 77.8 | 65 | diagonal:21,step:8,walk:35 |

## SLR-N06 · 东侧书院和游乐暗区
- 城市类型: education/recreation edge + ambiguous dark area
- 场景组合: 羽毛球场、书院、暗区、健身游乐场
- 操作重点: 东西向穿越、低照度/空洞判断、游乐设施确认
- 人工审核意图: 从迦南书院继续向东，检查暗区和健身游乐场是否对得上。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=279.3, turns=50, ascent=3, descent=3, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 迦南書院 | connector | -49,-2,-613 | -49,-2,-613 | 0.0 |
| 2 | via | 黑暗的地方 | primary | 16,-2,-593 | 16,-2,-593 | 0.0 |
| 3 | end | 健身游乐场 | primary | -15,-2,-651 | -15,-2,-651 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N06-S01 | 迦南書院 -> 黑暗的地方 | certified_static_reference | 160.0 | 138 | diagonal:50,step:4,walk:83 |
| SLR-N06-S02 | 黑暗的地方 -> 健身游乐场 | certified_static_reference | 119.3 | 105 | diagonal:37,walk:67 |

## SLR-N07 · 赛车场到教堂低层入口
- 城市类型: open recreation to religious interior transition
- 场景组合: 赛车场、教堂外部、楼梯、二楼入口
- 操作重点: 室外到室内转换、门/楼梯进入、垂直起点确认
- 人工审核意图: 从外部活动场地走到教堂低层入口，为室内路线接续。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=242.4, turns=73, ascent=12, descent=14, doors=4

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 赛车场 | primary | -147,6,-519 | -147,6,-519 | 0.0 |
| 2 | via | 基督教汇基堂 | primary | -113,-2,-535 | -113,-2,-535 | 0.0 |
| 3 | via | 教堂楼梯 | primary | -114,-2,-544 | -114,-2,-544 | 0.0 |
| 4 | end | 教堂2楼入口 | primary | -114,4,-545 | -114,4,-545 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N07-S01 | 赛车场 -> 基督教汇基堂 | certified_static_reference | 203.3 | 187 | diagonal:27,step:14,walk:145 |
| SLR-N07-S02 | 基督教汇基堂 -> 教堂楼梯 | certified_static_reference | 24.9 | 23 | diagonal:3,step:4,walk:15 |
| SLR-N07-S03 | 教堂楼梯 -> 教堂2楼入口 | certified_static_reference | 14.2 | 12 | diagonal:2,step:5,walk:4 |

## SLR-N08 · 教堂低层到三楼可走线
- 城市类型: indoor low/mid floor vertical route
- 场景组合: 二楼入口、二楼平台、暗楼梯、三楼暗处、三楼、楼梯2
- 操作重点: 楼梯、低照度、上下楼、平台转向
- 人工审核意图: 从教堂二楼入口沿已标楼梯和平台走到三楼及楼梯2，优先形成一条可审核室内线。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=266.1, turns=49, ascent=4, descent=10, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂2楼入口 | connector | -114,4,-545 | -114,4,-545 | 0.0 |
| 2 | via | 教堂2楼平台 | primary | -113,4,-568 | -113,4,-568 | 0.0 |
| 3 | via | 教堂2到3暗处楼梯 | primary | -114,4,-543 | -114,4,-543 | 0.0 |
| 4 | via | 教堂3楼暗处 | primary | -117,7,-540 | -117,7,-540 | 0.0 |
| 5 | via | 教堂3楼 | primary | -117,7,-600 | -117,7,-600 | 0.0 |
| 6 | end | 教堂楼梯2 | primary | -121,-2,-597 | -121,-2,-597 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N08-S01 | 教堂2楼入口 -> 教堂2楼平台 | certified_static_reference | 22.4 | 23 | diagonal:1,walk:21 |
| SLR-N08-S02 | 教堂2楼平台 -> 教堂2到3暗处楼梯 | certified_static_reference | 24.0 | 25 | walk:24 |
| SLR-N08-S03 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 | 123 | diagonal:16,step:2,walk:104 |
| SLR-N08-S04 | 教堂3楼暗处 -> 教堂3楼 | certified_static_reference | 61.9 | 60 | diagonal:7,walk:52 |
| SLR-N08-S05 | 教堂3楼 -> 教堂楼梯2 | certified_static_reference | 28.0 | 21 | diagonal:3,step:6,walk:11 |

## SLR-N09 · 教堂中高层问题段
- 城市类型: indoor upper-floor diagnostic route
- 场景组合: 三楼暗处、卡点、四楼暗处、五楼、六楼、六楼平台入口
- 操作重点: 卡点排查、暗处楼梯、高层平台、垂直连通诊断
- 人工审核意图: 把卡住点、四楼暗处和五六楼单独放在一条诊断路线，避免污染外部自然路线。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=94.3, turns=32, ascent=9, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂3楼暗处 | connector | -117,7,-540 | -117,7,-540 | 0.0 |
| 2 | via | 为什么这里卡住了 | primary | -112,14,-540 | -112,14,-540 | 0.0 |
| 3 | via | 教堂4楼暗处 | primary | -114,12,-544 | -114,13,-544 | 1.0 |
| 4 | via | 教堂5楼 | primary | -117,19,-601 | -117,19,-601 | 0.0 |
| 5 | via | 教堂6楼 | primary | -116,22,-601 | -116,22,-601 | 0.0 |
| 6 | end | 教堂6楼平台入口 | primary | -113,21,-594 | -113,22,-594 | 1.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N09-S01 | 教堂3楼暗处 -> 为什么这里卡住了 | no_path_found |  |  |  |
| SLR-N09-S02 | 为什么这里卡住了 -> 教堂4楼暗处 | no_path_found |  |  |  |
| SLR-N09-S03 | 教堂4楼暗处 -> 教堂5楼 | certified_static_reference | 75.8 | 71 | diagonal:8,step:6,walk:56 |
| SLR-N09-S04 | 教堂5楼 -> 教堂6楼 | certified_static_reference | 11.7 | 11 | diagonal:1,step:3,walk:6 |
| SLR-N09-S05 | 教堂6楼 -> 教堂6楼平台入口 | certified_static_reference | 6.8 | 7 | diagonal:2,walk:4 |

## SLR-N10 · 图书馆和蹲下门微操作
- 城市类型: indoor precise endpoint operation
- 场景组合: 六楼平台入口、蹲下门、图书馆
- 操作重点: 窄门、蹲下、精准终点确认
- 人工审核意图: 短路线专门核对蹲下门和图书馆这类精细终点。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=1.0, turns=0, ascent=0, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂6楼平台入口 | connector | -113,21,-594 | -113,22,-594 | 1.0 |
| 2 | via | 需要蹲下的门 | primary | -110,21,-594 | -110,21,-594 | 0.0 |
| 3 | end | 图书馆 | primary | -108,21,-594 | -108,21,-594 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N10-S01 | 教堂6楼平台入口 -> 需要蹲下的门 | no_path_found |  |  |  |
| SLR-N10-S02 | 需要蹲下的门 -> 图书馆 | certified_static_reference | 1.0 | 2 | walk:1 |
