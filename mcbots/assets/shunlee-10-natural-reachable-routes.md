# Shun Lee 本地标点 10 条任务语义路线与静态可达性
- 来源: `runtime/shun-lee-review-vnc/20260716_clean_v3_shun_lee_review_vnc/local-user-waypoints/shunlee-marked-waypoints.txt`
- World: `eval/snapshots/imported_1_21_1/shun-lee-clean-v3/world`
- 点数: 39；路线数: 10；primary 覆盖: 39/39
- 说明: `connector` 是为保持路线自然而重复出现的衔接点；覆盖统计只按 `primary` 计一次。
- 边界: 这是静态 world 几何寻路结果，不等于真人/agent 实走通过；`all_segments_certified` 最适合优先人工审核。

## 总览
- 路线状态: {"all_segments_certified": 7, "partial_static_route": 3}
- 路段状态: {"certified_static_reference": 26, "no_path_found": 3}
- 坐标贴近: {"exact_standable": 36, "snapped": 3}
- 非认证/失败路段数: 3

### 需要人工优先确认的路段
- SLR-N06 SLR-N06-S01: 顺利纪律宿舍2座 -> 顺利队宿舍3号楼 (no_path_found)
- SLR-N09 SLR-N09-S01: 为什么这里卡住了 -> 教堂4楼暗处 (no_path_found)
- SLR-N10 SLR-N10-S02: 教堂6楼平台入口 -> 需要蹲下的门 (no_path_found)

## SLR-N01 · 从家出发去赛车场晨练
- 城市类型: residential origin to recreation
- 场景组合: 住宅起点、宿舍区入口、室外活动场地
- 操作重点: 从家出发、出入口识别、到达开放活动场地
- 人工审核意图: 你住在楼8。出门先到顺利消防宿舍区入口确认方向，然后走到赛车场晨练。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=288.1, turns=100, ascent=6, descent=10, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 楼8 | primary | -185,10,-619 | -185,10,-619 | 0.0 |
| 2 | via | 顺利消防宿舍区入口 | primary | -267,10,-549 | -267,10,-549 | 0.0 |
| 3 | end | 赛车场 | primary | -147,6,-519 | -147,6,-519 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N01-S01 | 楼8 -> 顺利消防宿舍区入口 | certified_static_reference | 145.8 | 130 | diagonal:37,step:2,walk:90 |
| SLR-N01-S02 | 顺利消防宿舍区入口 -> 赛车场 | certified_static_reference | 142.3 | 131 | diagonal:18,step:11,walk:101 |

## SLR-N02 · 从家出发去吃饭再打羽毛球
- 城市类型: residential origin to daily meal/recreation
- 场景组合: 住宅起点、教堂餐厅、羽毛球场
- 操作重点: 日常生活目的、餐饮点确认、运动场地到达
- 人工审核意图: 你住在楼7。先去教堂餐厅吃饭，之后去羽毛球场参加活动。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=463.3, turns=130, ascent=5, descent=17, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 楼7 | primary | -196,10,-657 | -196,10,-657 | 0.0 |
| 2 | via | 教堂餐厅 | primary | -107,-2,-596 | -107,-2,-596 | 0.0 |
| 3 | end | 羽毛球场 | primary | -92,-2,-573 | -92,-2,-573 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N02-S01 | 楼7 -> 教堂餐厅 | certified_static_reference | 434.3 | 389 | diagonal:90,step:16,walk:282 |
| SLR-N02-S02 | 教堂餐厅 -> 羽毛球场 | certified_static_reference | 29.0 | 25 | diagonal:12,walk:12 |

## SLR-N03 · 从家出发送孩子去学校片区
- 城市类型: residential origin to school/childcare
- 场景组合: 住宅起点、学校篮球场、扶幼中心
- 操作重点: 学校周边定位、照护设施入口、操场边界
- 人工审核意图: 你住在楼6。早上先经过盛德学校篮球场，再到盛德扶幼中心。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=600.0, turns=121, ascent=4, descent=16, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 楼6 | primary | -211,10,-696 | -211,10,-696 | 0.0 |
| 2 | via | 盛德学校篮球场 | primary | -206,-2,-550 | -206,-2,-550 | 0.0 |
| 3 | end | 盛德扶幼中心 | primary | -211,-2,-599 | -211,-2,-599 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N03-S01 | 楼6 -> 盛德学校篮球场 | certified_static_reference | 487.4 | 441 | diagonal:93,step:15,walk:332 |
| SLR-N03-S02 | 盛德学校篮球场 -> 盛德扶幼中心 | certified_static_reference | 112.6 | 90 | diagonal:57,walk:32 |

## SLR-N04 · 从值班宿舍去消防局再坐车
- 城市类型: service housing to emergency facility/transit
- 场景组合: 值班宿舍、消防局门口、消防局、公交站
- 操作重点: 公共服务设施到达、门口确认、交通接驳
- 人工审核意图: 你从顺利消防宿舍楼5出发，到顺利消防局门口报到，进入消防局确认位置，然后去消防公交车站坐车。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=549.2, turns=149, ascent=3, descent=16, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利消防宿舍楼5 | primary | -248,10,-673 | -248,10,-673 | 0.0 |
| 2 | via | 顺利消防局门口 | primary | -90,-3,-623 | -90,-3,-623 | 0.0 |
| 3 | via | 顺利消防局 | primary | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 4 | end | 消防公交车站 | primary | -163,-3,-696 | -163,-3,-696 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N04-S01 | 顺利消防宿舍楼5 -> 顺利消防局门口 | certified_static_reference | 412.0 | 376 | diagonal:73,step:14,walk:288 |
| SLR-N04-S02 | 顺利消防局门口 -> 顺利消防局 | certified_static_reference | 31.4 | 32 | step:1,walk:30 |
| SLR-N04-S03 | 顺利消防局 -> 消防公交车站 | certified_static_reference | 105.8 | 96 | diagonal:25,step:1,walk:69 |

## SLR-N05 · 从宿舍去训练再去足球场集合
- 城市类型: institutional housing to sports field
- 场景组合: 纪律部队宿舍、操场、同伴楼栋、足球场正门
- 操作重点: 训练场地、集合点、球场入口
- 人工审核意图: 你从顺利部队宿舍1号楼出发，先到操场训练，再到顺利纪律部队2号楼找同伴，最后去顺利足球场正门集合。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=458.4, turns=138, ascent=7, descent=18, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利部队宿舍1号楼 | primary | -268,10,-574 | -268,10,-574 | 0.0 |
| 2 | via | 顺利部队操场 | primary | -280,10,-563 | -280,10,-563 | 0.0 |
| 3 | via | 顺利纪律部队2号楼 | primary | -287,10,-618 | -287,10,-618 | 0.0 |
| 4 | end | 顺利足球场正门 | primary | -142,-1,-671 | -142,-1,-671 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N05-S01 | 顺利部队宿舍1号楼 -> 顺利部队操场 | certified_static_reference | 16.5 | 13 | diagonal:9,step:1,walk:2 |
| SLR-N05-S02 | 顺利部队操场 -> 顺利纪律部队2号楼 | certified_static_reference | 66.0 | 60 | diagonal:15,step:2,walk:42 |
| SLR-N05-S03 | 顺利纪律部队2号楼 -> 顺利足球场正门 | certified_static_reference | 375.9 | 343 | diagonal:62,step:16,walk:264 |

## SLR-N06 · 从远端宿舍去五人制球场
- 城市类型: residential origin to local sports pitch
- 场景组合: 远端宿舍起点、同伴宿舍、球场侧门、五人制足球场
- 操作重点: 起点定位、找同伴、侧门进入、球场终点
- 人工审核意图: 你住在顺利纪律宿舍2座。先去顺利队宿舍3号楼找同伴，再从顺足侧门进入，最后到五人制足球场。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=471.7, turns=115, ascent=6, descent=17, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 顺利纪律宿舍2座 | primary | -268,2,-744 | -270,2,-741 | 3.6 |
| 2 | via | 顺利队宿舍3号楼 | primary | -300,10,-664 | -300,10,-664 | 0.0 |
| 3 | via | 顺足侧门 | primary | -118,-2,-674 | -118,-2,-674 | 0.0 |
| 4 | end | 顺利邨游乐场五人制足球场 | primary | -137,-1,-694 | -137,-1,-694 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N06-S01 | 顺利纪律宿舍2座 -> 顺利队宿舍3号楼 | no_path_found |  |  |  |
| SLR-N06-S02 | 顺利队宿舍3号楼 -> 顺足侧门 | certified_static_reference | 444.2 | 408 | diagonal:70,step:16,walk:321 |
| SLR-N06-S03 | 顺足侧门 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 27.5 | 21 | diagonal:17,step:1,walk:2 |

## SLR-N07 · 放学后从书院去游乐场
- 城市类型: education edge to recreation
- 场景组合: 书院、暗处通道、健身游乐场
- 操作重点: 学校边缘、低照度/空洞判断、游乐设施到达
- 人工审核意图: 你从迦南書院出来，经过需要重点人工确认的黑暗区域，最后到健身游乐场。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=279.3, turns=50, ascent=3, descent=3, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 迦南書院 | primary | -49,-2,-613 | -49,-2,-613 | 0.0 |
| 2 | via | 黑暗的地方 | primary | 16,-2,-593 | 16,-2,-593 | 0.0 |
| 3 | end | 健身游乐场 | primary | -15,-2,-651 | -15,-2,-651 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N07-S01 | 迦南書院 -> 黑暗的地方 | certified_static_reference | 160.0 | 138 | diagonal:50,step:4,walk:83 |
| SLR-N07-S02 | 黑暗的地方 -> 健身游乐场 | certified_static_reference | 119.3 | 105 | diagonal:37,walk:67 |

## SLR-N08 · 去教堂活动并找到三楼房间
- 城市类型: religious entrance to indoor mid floor
- 场景组合: 教堂入口、楼梯、二楼平台、暗楼梯、三楼房间
- 操作重点: 室外到室内转换、楼梯进入、低照度楼梯、三楼定位
- 人工审核意图: 你要去基督教汇基堂参加活动。从教堂入口进来，找到楼梯，上到二楼平台，经由通往三楼的暗楼梯，最后找到三楼房间和楼梯2。
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=305.3, turns=69, ascent=12, descent=12, doors=2

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 基督教汇基堂 | primary | -113,-2,-535 | -113,-2,-535 | 0.0 |
| 2 | via | 教堂楼梯 | primary | -114,-2,-544 | -114,-2,-544 | 0.0 |
| 3 | via | 教堂2楼入口 | primary | -114,4,-545 | -114,4,-545 | 0.0 |
| 4 | via | 教堂2楼平台 | primary | -113,4,-568 | -113,4,-568 | 0.0 |
| 5 | via | 教堂2到3暗处楼梯 | primary | -114,4,-543 | -114,4,-543 | 0.0 |
| 6 | via | 教堂3楼暗处 | primary | -117,7,-540 | -117,7,-540 | 0.0 |
| 7 | via | 教堂3楼 | primary | -117,7,-600 | -117,7,-600 | 0.0 |
| 8 | end | 教堂楼梯2 | primary | -121,-2,-597 | -121,-2,-597 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N08-S01 | 基督教汇基堂 -> 教堂楼梯 | certified_static_reference | 24.9 | 23 | diagonal:3,step:4,walk:15 |
| SLR-N08-S02 | 教堂楼梯 -> 教堂2楼入口 | certified_static_reference | 14.2 | 12 | diagonal:2,step:5,walk:4 |
| SLR-N08-S03 | 教堂2楼入口 -> 教堂2楼平台 | certified_static_reference | 22.4 | 23 | diagonal:1,walk:21 |
| SLR-N08-S04 | 教堂2楼平台 -> 教堂2到3暗处楼梯 | certified_static_reference | 24.0 | 25 | walk:24 |
| SLR-N08-S05 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 | 123 | diagonal:16,step:2,walk:104 |
| SLR-N08-S06 | 教堂3楼暗处 -> 教堂3楼 | certified_static_reference | 61.9 | 60 | diagonal:7,walk:52 |
| SLR-N08-S07 | 教堂3楼 -> 教堂楼梯2 | certified_static_reference | 28.0 | 21 | diagonal:3,step:6,walk:11 |

## SLR-N09 · 教堂暗处维护检查
- 城市类型: indoor maintenance/obstacle check
- 场景组合: 卡点、四楼暗处、五楼出口
- 操作重点: 卡点复核、暗处检查、楼层出口确认
- 人工审核意图: 你是教堂工作人员。去检查之前容易卡住的位置和四楼暗处，确认后到五楼出口位置结束。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=75.8, turns=19, ascent=6, descent=0, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 为什么这里卡住了 | primary | -112,14,-540 | -112,14,-540 | 0.0 |
| 2 | via | 教堂4楼暗处 | primary | -114,12,-544 | -114,13,-544 | 1.0 |
| 3 | end | 教堂5楼 | primary | -117,19,-601 | -117,19,-601 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N09-S01 | 为什么这里卡住了 -> 教堂4楼暗处 | no_path_found |  |  |  |
| SLR-N09-S02 | 教堂4楼暗处 -> 教堂5楼 | certified_static_reference | 75.8 | 71 | diagonal:8,step:6,walk:56 |

## SLR-N10 · 从六楼去图书馆取书
- 城市类型: indoor upper-floor library errand
- 场景组合: 六楼、六楼平台入口、蹲下门、图书馆
- 操作重点: 高层平台、窄门/蹲下、图书馆终点确认
- 人工审核意图: 你在教堂六楼，要去图书馆取书。先到六楼平台入口，通过需要蹲下的门，最后到图书馆。
- 静态状态: partial_static_route；难度预标: D5_blocked_or_uncertified_static_route
- 指标: length=7.8, turns=3, ascent=0, descent=1, doors=0

| # | role | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---:|---:|---:|
| 1 | start | 教堂6楼 | primary | -116,22,-601 | -116,22,-601 | 0.0 |
| 2 | via | 教堂6楼平台入口 | primary | -113,21,-594 | -113,22,-594 | 1.0 |
| 3 | via | 需要蹲下的门 | primary | -110,21,-594 | -110,21,-594 | 0.0 |
| 4 | end | 图书馆 | primary | -108,21,-594 | -108,21,-594 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N10-S01 | 教堂6楼 -> 教堂6楼平台入口 | certified_static_reference | 6.8 | 7 | diagonal:2,walk:4 |
| SLR-N10-S02 | 教堂6楼平台入口 -> 需要蹲下的门 | no_path_found |  |  |  |
| SLR-N10-S03 | 需要蹲下的门 -> 图书馆 | certified_static_reference | 1.0 | 2 | walk:1 |
