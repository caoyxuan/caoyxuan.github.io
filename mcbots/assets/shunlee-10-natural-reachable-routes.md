# Shun Lee 本地标点 10 条自然路线与静态可达性
- 来源: `runtime/shun-lee-review-vnc/20260716_clean_v3_shun_lee_review_vnc/local-user-waypoints/shunlee-marked-waypoints.txt`
- World: `eval/snapshots/imported_1_21_1/shun-lee-clean-v3/world`
- 点数: 39；路线数: 10；primary 覆盖: 39/39
- 说明: `connector` 是为保持路线自然而重复出现的衔接点；覆盖统计只按 `primary` 计一次。
- 边界: 这是静态 world 几何寻路结果，不等于真人/agent 实走通过；`all_segments_certified` 最适合优先人工审核。

## 总览
- 路线状态: {"all_segments_certified": 5, "all_segments_found_uncertified": 1, "partial_static_route": 4}
- 路段状态: {"certified_static_reference": 28, "no_path_found": 5, "static_path_upper_bound": 1}
- 坐标贴近: {"exact_standable": 36, "snapped": 3}
- 非认证/失败路段数: 6

### 需要人工优先确认的路段
- SLR-N01 SLR-N01-S03: 楼6 -> 消防公交车站 (static_path_upper_bound)
- SLR-N04 SLR-N04-S02: 顺利消防宿舍楼5 -> 顺利纪律宿舍2座 (no_path_found)
- SLR-N08 SLR-N08-S04: 教堂3楼暗处 -> 为什么这里卡住了 (no_path_found)
- SLR-N08 SLR-N08-S05: 为什么这里卡住了 -> 教堂4楼暗处 (no_path_found)
- SLR-N09 SLR-N09-S02: 教堂3楼 -> 教堂5楼 (no_path_found)
- SLR-N10 SLR-N10-S01: 教堂6楼平台入口 -> 需要蹲下的门 (no_path_found)

## SLR-N01 · 住宅塔楼到公交和球场边缘
- 城市类型: high-rise estate spine + transit/sports edge
- 场景组合: 住宅塔楼、楼间平台、公交边缘、开放运动场
- 操作重点: 长走廊式步行、室外开阔地确认、入口边界判断
- 人工审核意图: 从顺利邨塔楼群顺着南侧生活动线走到公交和球场边缘。
- 静态状态: all_segments_found_uncertified；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=634.1, turns=148, ascent=5, descent=16, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 楼8 | primary | -185,10,-619 | -185,10,-619 | 0.0 |
| 2 | via | 楼7 | primary | -196,10,-657 | -196,10,-657 | 0.0 |
| 3 | via | 楼6 | primary | -211,10,-696 | -211,10,-696 | 0.0 |
| 4 | via | 消防公交车站 | primary | -163,-3,-696 | -163,-3,-696 | 0.0 |
| 5 | end | 顺利邨游乐场五人制足球场 | primary | -137,-1,-694 | -137,-1,-694 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N01-S01 | 楼8 -> 楼7 | certified_static_reference | 46.2 | 41 | diagonal:15,walk:25 |
| SLR-N01-S02 | 楼7 -> 楼6 | certified_static_reference | 44.8 | 40 | diagonal:14,walk:25 |
| SLR-N01-S03 | 楼6 -> 消防公交车站 | static_path_upper_bound | 476.2 | 434 | diagonal:86,step:16,walk:331 |
| SLR-N01-S04 | 消防公交车站 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 66.9 | 63 | diagonal:10,step:1,walk:51 |

## SLR-N02 · 消防局到足球场入口环
- 城市类型: emergency service frontage + sports access
- 场景组合: 消防局、门口、足球场正门、侧门、五人制足球场
- 操作重点: 沿街门口识别、场地围栏/入口判断、短距离转向
- 人工审核意图: 沿公共服务设施和足球场边界检查入口是否清楚。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=170.2, turns=44, ascent=3, descent=1, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利消防局门口 | primary | -90,-3,-623 | -90,-3,-623 | 0.0 |
| 2 | via | 顺利消防局 | primary | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 3 | via | 顺利足球场正门 | primary | -142,-1,-671 | -142,-1,-671 | 0.0 |
| 4 | via | 顺足侧门 | primary | -118,-2,-674 | -118,-2,-674 | 0.0 |
| 5 | end | 顺利邨游乐场五人制足球场 | connector | -137,-1,-694 | -137,-1,-694 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N02-S01 | 顺利消防局门口 -> 顺利消防局 | certified_static_reference | 31.4 | 32 | step:1,walk:30 |
| SLR-N02-S02 | 顺利消防局 -> 顺利足球场正门 | certified_static_reference | 85.9 | 77 | diagonal:23,step:1,walk:52 |
| SLR-N02-S03 | 顺利足球场正门 -> 顺足侧门 | certified_static_reference | 25.4 | 26 | diagonal:1,walk:24 |
| SLR-N02-S04 | 顺足侧门 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 27.5 | 21 | diagonal:17,step:1,walk:2 |

## SLR-N03 · 纪律部队宿舍核心
- 城市类型: institutional residential estate
- 场景组合: 宿舍入口、楼栋、操场、内部道路
- 操作重点: 院区内部连通、平台高度变化、楼栋间定位
- 人工审核意图: 按院区内部动线核对宿舍楼、操场和入口。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=158.5, turns=47, ascent=4, descent=4, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利消防宿舍区入口 | primary | -267,10,-549 | -267,10,-549 | 0.0 |
| 2 | via | 顺利部队宿舍1号楼 | primary | -268,10,-574 | -268,10,-574 | 0.0 |
| 3 | via | 顺利部队操场 | primary | -280,10,-563 | -280,10,-563 | 0.0 |
| 4 | via | 顺利纪律部队2号楼 | primary | -287,10,-618 | -287,10,-618 | 0.0 |
| 5 | end | 顺利队宿舍3号楼 | primary | -300,10,-664 | -300,10,-664 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N03-S01 | 顺利消防宿舍区入口 -> 顺利部队宿舍1号楼 | certified_static_reference | 26.1 | 25 | diagonal:1,step:4,walk:19 |
| SLR-N03-S02 | 顺利部队宿舍1号楼 -> 顺利部队操场 | certified_static_reference | 16.5 | 13 | diagonal:9,step:1,walk:2 |
| SLR-N03-S03 | 顺利部队操场 -> 顺利纪律部队2号楼 | certified_static_reference | 66.0 | 60 | diagonal:15,step:2,walk:42 |
| SLR-N03-S04 | 顺利纪律部队2号楼 -> 顺利队宿舍3号楼 | certified_static_reference | 50.0 | 46 | diagonal:12,walk:33 |

## SLR-N04 · 纪律宿舍坡地远端
- 城市类型: estate hillside/peripheral link
- 场景组合: 远端宿舍楼、坡地边缘、楼座转换
- 操作重点: 高差确认、边缘道路识别、长距离定位
- 人工审核意图: 从已确认宿舍核心继续检查西南远端宿舍和坡地边缘。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=54.3, turns=5, ascent=0, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利队宿舍3号楼 | connector | -300,10,-664 | -300,10,-664 | 0.0 |
| 2 | via | 顺利消防宿舍楼5 | primary | -248,10,-673 | -248,10,-673 | 0.0 |
| 3 | end | 顺利纪律宿舍2座 | primary | -268,2,-744 | -270,2,-741 | 3.6 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N04-S01 | 顺利队宿舍3号楼 -> 顺利消防宿舍楼5 | certified_static_reference | 54.3 | 52 | diagonal:8,walk:43 |
| SLR-N04-S02 | 顺利消防宿舍楼5 -> 顺利纪律宿舍2座 | no_path_found |  |  |  |

## SLR-N05 · 盛德学校到教堂生活设施
- 城市类型: school/civic/religious mixed frontage
- 场景组合: 篮球场、扶幼中心、餐厅、羽毛球场
- 操作重点: 学校周边、庭院/球场边界、建筑入口附近定位
- 人工审核意图: 沿学校和教堂旁的日常设施做一条低层生活线。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=272.5, turns=60, ascent=5, descent=5, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 盛德学校篮球场 | primary | -206,-2,-550 | -206,-2,-550 | 0.0 |
| 2 | via | 盛德扶幼中心 | primary | -211,-2,-599 | -211,-2,-599 | 0.0 |
| 3 | via | 教堂餐厅 | primary | -107,-2,-596 | -107,-2,-596 | 0.0 |
| 4 | end | 羽毛球场 | primary | -92,-2,-573 | -92,-2,-573 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N05-S01 | 盛德学校篮球场 -> 盛德扶幼中心 | certified_static_reference | 112.6 | 90 | diagonal:57,walk:32 |
| SLR-N05-S02 | 盛德扶幼中心 -> 教堂餐厅 | certified_static_reference | 130.9 | 120 | diagonal:18,step:8,walk:93 |
| SLR-N05-S03 | 教堂餐厅 -> 羽毛球场 | certified_static_reference | 29.0 | 25 | diagonal:12,walk:12 |

## SLR-N06 · 东侧书院和游乐暗区
- 城市类型: education/recreation edge + ambiguous dark area
- 场景组合: 羽毛球场、书院、暗区、健身游乐场
- 操作重点: 东西向穿越、低照度/空洞判断、游乐设施确认
- 人工审核意图: 从已确认球场继续向东，检查书院、暗区和游乐场是否对得上。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=357.1, turns=67, ascent=8, descent=8, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 羽毛球场 | connector | -92,-2,-573 | -92,-2,-573 | 0.0 |
| 2 | via | 迦南書院 | primary | -49,-2,-613 | -49,-2,-613 | 0.0 |
| 3 | via | 黑暗的地方 | primary | 16,-2,-593 | 16,-2,-593 | 0.0 |
| 4 | end | 健身游乐场 | primary | -15,-2,-651 | -15,-2,-651 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N06-S01 | 羽毛球场 -> 迦南書院 | certified_static_reference | 77.8 | 65 | diagonal:21,step:8,walk:35 |
| SLR-N06-S02 | 迦南書院 -> 黑暗的地方 | certified_static_reference | 160.0 | 138 | diagonal:50,step:4,walk:83 |
| SLR-N06-S03 | 黑暗的地方 -> 健身游乐场 | certified_static_reference | 119.3 | 105 | diagonal:37,walk:67 |

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

## SLR-N08 · 教堂低层暗楼梯诊断
- 城市类型: indoor low/mid floor diagnostic
- 场景组合: 二楼平台、暗楼梯、三楼暗处、卡点、四楼暗处
- 操作重点: 楼梯、低照度、可能卡点、上下楼确认
- 人工审核意图: 沿低层到暗处楼梯逐点检查，重点看是否真的能走通。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=176.2, turns=27, ascent=3, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂2楼入口 | connector | -114,4,-545 | -114,4,-545 | 0.0 |
| 2 | via | 教堂2楼平台 | primary | -113,4,-568 | -113,4,-568 | 0.0 |
| 3 | via | 教堂2到3暗处楼梯 | primary | -114,4,-543 | -114,4,-543 | 0.0 |
| 4 | via | 教堂3楼暗处 | primary | -117,7,-540 | -117,7,-540 | 0.0 |
| 5 | via | 为什么这里卡住了 | primary | -112,14,-540 | -112,14,-540 | 0.0 |
| 6 | end | 教堂4楼暗处 | primary | -114,12,-544 | -114,13,-544 | 1.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N08-S01 | 教堂2楼入口 -> 教堂2楼平台 | certified_static_reference | 22.4 | 23 | diagonal:1,walk:21 |
| SLR-N08-S02 | 教堂2楼平台 -> 教堂2到3暗处楼梯 | certified_static_reference | 24.0 | 25 | walk:24 |
| SLR-N08-S03 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 | 123 | diagonal:16,step:2,walk:104 |
| SLR-N08-S04 | 教堂3楼暗处 -> 为什么这里卡住了 | no_path_found |  |  |  |
| SLR-N08-S05 | 为什么这里卡住了 -> 教堂4楼暗处 | no_path_found |  |  |  |

## SLR-N09 · 教堂中高层垂直线
- 城市类型: indoor upper-floor vertical route
- 场景组合: 楼梯2、三楼、五楼、六楼、六楼平台入口
- 操作重点: 多层楼梯、垂直导航、平台入口判断
- 人工审核意图: 把教堂中高层作为单独垂直路线，避免和外部路线混在一起。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=40.6, turns=24, ascent=24, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂楼梯2 | primary | -121,-2,-597 | -121,-2,-597 | 0.0 |
| 2 | via | 教堂3楼 | primary | -117,7,-600 | -117,7,-600 | 0.0 |
| 3 | via | 教堂5楼 | primary | -117,19,-601 | -117,19,-601 | 0.0 |
| 4 | via | 教堂6楼 | primary | -116,22,-601 | -116,22,-601 | 0.0 |
| 5 | end | 教堂6楼平台入口 | primary | -113,21,-594 | -113,22,-594 | 1.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N09-S01 | 教堂楼梯2 -> 教堂3楼 | certified_static_reference | 22.1 | 19 | diagonal:1,step:9,walk:8 |
| SLR-N09-S02 | 教堂3楼 -> 教堂5楼 | no_path_found |  |  |  |
| SLR-N09-S03 | 教堂5楼 -> 教堂6楼 | certified_static_reference | 11.7 | 11 | diagonal:1,step:3,walk:6 |
| SLR-N09-S04 | 教堂6楼 -> 教堂6楼平台入口 | certified_static_reference | 6.8 | 7 | diagonal:2,walk:4 |

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
