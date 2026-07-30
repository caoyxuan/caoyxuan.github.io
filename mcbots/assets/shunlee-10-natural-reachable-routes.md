# Shun Lee 本地标点 10 条任务语义路线与静态可达性
- 来源: `runtime/shun-lee-review-vnc/20260716_clean_v3_shun_lee_review_vnc/local-user-waypoints/shunlee-marked-waypoints.txt`
- World: `eval/snapshots/imported_1_21_1/shun-lee-clean-v3/world`
- 点数: 39；路线数: 10；primary 覆盖: 30/39
- 说明: `connector` 是为保持路线自然而重复出现的衔接点；覆盖统计只按 `primary` 计一次。
- 题面分层: `prompt` 点可进入 Agent 题面；`evaluator_hidden` 点和 hidden operation 仅供 evaluator 约束/审核，禁止泄露具体走法。
- 语义策略: 不再为了标点覆盖率把每个可站点硬塞进十条路线；有效但当前不自然的点保留在 alternate pool。
- 边界: 这是静态 world 几何寻路结果，不等于真人/agent 实走通过；`all_segments_certified` 最适合优先人工审核。

## 总览
- 路线状态: {"all_segments_certified": 10}
- 路段状态: {"certified_static_reference": 25}
- 坐标贴近: {"exact_standable": 36, "snapped": 3}
- Agent 可见语义点: 20；evaluator hidden 点: 11
- Alternate pool: ["教堂5楼", "教堂楼梯2", "顺利消防局门口", "顺利足球场正门", "黑暗的地方"]
- 非认证/失败路段数: 0

## SLR-N01 · 从楼8去赛车场晨练
- 城市类型: residential origin to recreation
- 场景组合: 住宅起点、街区步行、室外活动场地
- 操作重点: 从家出发、街区定向、到达开放活动场地
- Agent 可见意图: 你住在楼8。早上从家出发，步行去赛车场晨练。
- Agent 可见点: ["楼8", "赛车场"]
- Evaluator hidden 点: ["顺利消防宿舍区入口"]
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=288.1, turns=100, ascent=6, descent=10, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 楼8 | primary | -185,10,-619 | -185,10,-619 | 0.0 |
| 2 | via | evaluator_hidden | 顺利消防宿舍区入口 | connector | -267,10,-549 | -267,10,-549 | 0.0 |
| 3 | end | prompt | 赛车场 | primary | -147,6,-519 | -147,6,-519 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N01-S01 | 楼8 -> 顺利消防宿舍区入口 | certified_static_reference | 145.8 | 130 | diagonal:37,step:2,walk:90 |
| SLR-N01-S02 | 顺利消防宿舍区入口 -> 赛车场 | certified_static_reference | 142.3 | 131 | diagonal:18,step:11,walk:101 |

## SLR-N02 · 从楼7吃饭后去打羽毛球
- 城市类型: residential origin to daily meal/recreation
- 场景组合: 住宅起点、教堂餐厅、羽毛球场
- 操作重点: 日常生活目的、餐饮点确认、运动场地到达
- Agent 可见意图: 你从楼7出发，先去教堂餐厅吃饭，之后到羽毛球场参加活动。
- Agent 可见点: ["楼7", "教堂餐厅", "羽毛球场"]
- Evaluator hidden 点: []
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=463.3, turns=130, ascent=5, descent=17, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 楼7 | primary | -196,10,-657 | -196,10,-657 | 0.0 |
| 2 | via | prompt | 教堂餐厅 | primary | -107,-2,-596 | -107,-2,-596 | 0.0 |
| 3 | end | prompt | 羽毛球场 | primary | -92,-2,-573 | -92,-2,-573 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N02-S01 | 楼7 -> 教堂餐厅 | certified_static_reference | 434.3 | 389 | diagonal:90,step:16,walk:282 |
| SLR-N02-S02 | 教堂餐厅 -> 羽毛球场 | certified_static_reference | 29.0 | 25 | diagonal:12,walk:12 |

## SLR-N03 · 从楼6去扶幼中心
- 城市类型: residential origin to school/childcare
- 场景组合: 住宅起点、学校片区、扶幼中心
- 操作重点: 住宅出发、学校片区定位、照护设施到达
- Agent 可见意图: 早上从楼6出发，把孩子送到盛德扶幼中心。
- Agent 可见点: ["楼6", "盛德扶幼中心"]
- Evaluator hidden 点: []
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=432.1, turns=104, ascent=4, descent=16, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 楼6 | primary | -211,10,-696 | -211,10,-696 | 0.0 |
| 2 | end | prompt | 盛德扶幼中心 | primary | -211,-2,-599 | -211,-2,-599 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N03-S01 | 楼6 -> 盛德扶幼中心 | certified_static_reference | 432.1 | 389 | diagonal:85,step:15,walk:288 |

## SLR-N04 · 从值班宿舍办事后去坐车
- 城市类型: service housing to emergency facility/transit
- 场景组合: 值班宿舍、消防局、公交站
- 操作重点: 公共服务设施到达、办事后交通接驳
- Agent 可见意图: 你从顺利消防宿舍楼5出发，到顺利消防局交接物品，办完后去消防公交车站乘车。
- Agent 可见点: ["顺利消防宿舍楼5", "顺利消防局", "消防公交车站"]
- Evaluator hidden 点: []
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=486.5, turns=128, ascent=1, descent=14, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 顺利消防宿舍楼5 | primary | -248,10,-673 | -248,10,-673 | 0.0 |
| 2 | via | prompt | 顺利消防局 | primary | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 3 | end | prompt | 消防公交车站 | primary | -163,-3,-696 | -163,-3,-696 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N04-S01 | 顺利消防宿舍楼5 -> 顺利消防局 | certified_static_reference | 380.8 | 348 | diagonal:68,step:12,walk:267 |
| SLR-N04-S02 | 顺利消防局 -> 消防公交车站 | certified_static_reference | 105.8 | 96 | diagonal:25,step:1,walk:69 |

## SLR-N05 · 从宿舍区入口去3号楼找同伴
- 城市类型: institutional housing internal errand
- 场景组合: 宿舍区入口、高平台院落、宿舍楼终点
- 操作重点: 园区入口识别、平台内定向、楼栋到达
- Agent 可见意图: 你从顺利消防宿舍区入口进入，去顺利队宿舍3号楼找同伴。
- Agent 可见点: ["顺利消防宿舍区入口", "顺利队宿舍3号楼"]
- Evaluator hidden 点: ["顺利部队宿舍1号楼", "顺利部队操场", "顺利纪律部队2号楼"]
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=158.5, turns=47, ascent=4, descent=4, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 顺利消防宿舍区入口 | primary | -267,10,-549 | -267,10,-549 | 0.0 |
| 2 | via | evaluator_hidden | 顺利部队宿舍1号楼 | primary | -268,10,-574 | -268,10,-574 | 0.0 |
| 3 | via | evaluator_hidden | 顺利部队操场 | primary | -280,10,-563 | -280,10,-563 | 0.0 |
| 4 | via | evaluator_hidden | 顺利纪律部队2号楼 | primary | -287,10,-618 | -287,10,-618 | 0.0 |
| 5 | end | prompt | 顺利队宿舍3号楼 | primary | -300,10,-664 | -300,10,-664 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N05-S01 | 顺利消防宿舍区入口 -> 顺利部队宿舍1号楼 | certified_static_reference | 26.1 | 25 | diagonal:1,step:4,walk:19 |
| SLR-N05-S02 | 顺利部队宿舍1号楼 -> 顺利部队操场 | certified_static_reference | 16.5 | 13 | diagonal:9,step:1,walk:2 |
| SLR-N05-S03 | 顺利部队操场 -> 顺利纪律部队2号楼 | certified_static_reference | 66.0 | 60 | diagonal:15,step:2,walk:42 |
| SLR-N05-S04 | 顺利纪律部队2号楼 -> 顺利队宿舍3号楼 | certified_static_reference | 50.0 | 46 | diagonal:12,walk:33 |

## SLR-N06 · 消防局下班后去踢球
- 城市类型: emergency facility to local sports pitch
- 场景组合: 消防局起点、街区步行、五人制足球场
- 操作重点: 公共服务设施出发、球场边界识别、运动场到达
- Agent 可见意图: 你从顺利消防局出发，去顺利邨游乐场五人制足球场参加球赛。
- Agent 可见点: ["顺利消防局", "顺利邨游乐场五人制足球场"]
- Evaluator hidden 点: ["顺足侧门"]
- Hidden operation requirements: [{"evidence_status": "pending_live_walkthrough", "operation": "reviewed_entrance_selection", "prompt_exposure": "forbidden", "requirement_id": "SLR-N06-H01", "trigger_waypoints": ["顺足侧门"]}]
- 静态状态: all_segments_certified；难度预标: D2_medium_estate_static
- 指标: length=126.6, turns=23, ascent=5, descent=4, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 顺利消防局 | connector | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 2 | via | evaluator_hidden | 顺足侧门 | primary | -118,-2,-674 | -118,-2,-674 | 0.0 |
| 3 | end | prompt | 顺利邨游乐场五人制足球场 | primary | -137,-1,-694 | -137,-1,-694 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N06-S01 | 顺利消防局 -> 顺足侧门 | certified_static_reference | 99.1 | 87 | diagonal:22,step:5,walk:59 |
| SLR-N06-S02 | 顺足侧门 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 27.5 | 21 | diagonal:17,step:1,walk:2 |

## SLR-N07 · 从学校片区去健身游乐场
- 城市类型: school recreation to public recreation
- 场景组合: 学校篮球场、街区过渡、健身游乐场
- 操作重点: 学校片区出发、跨街区定向、游乐设施到达
- Agent 可见意图: 篮球活动结束后，从盛德学校篮球场出发，去健身游乐场继续锻炼。
- Agent 可见点: ["盛德学校篮球场", "健身游乐场"]
- Evaluator hidden 点: ["迦南書院"]
- Hidden operation requirements: []
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=358.0, turns=50, ascent=4, descent=4, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 盛德学校篮球场 | primary | -206,-2,-550 | -206,-2,-550 | 0.0 |
| 2 | via | evaluator_hidden | 迦南書院 | primary | -49,-2,-613 | -49,-2,-613 | 0.0 |
| 3 | end | prompt | 健身游乐场 | primary | -15,-2,-651 | -15,-2,-651 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N07-S01 | 盛德学校篮球场 -> 迦南書院 | certified_static_reference | 284.9 | 254 | diagonal:73,step:4,walk:176 |
| SLR-N07-S02 | 迦南書院 -> 健身游乐场 | certified_static_reference | 73.1 | 72 | diagonal:1,step:4,walk:66 |

## SLR-N08 · 进入教堂去三楼参加活动
- 城市类型: religious entrance to indoor mid floor
- 场景组合: 教堂入口、室内垂直通道、三楼活动室
- 操作重点: 室外到室内转换、垂直移动、楼层定位
- Agent 可见意图: 从基督教汇基堂入口进入，沿室内通道上到三楼活动室。
- Agent 可见点: ["基督教汇基堂", "教堂3楼"]
- Evaluator hidden 点: ["教堂楼梯", "教堂2楼入口", "教堂2到3暗处楼梯", "教堂3楼暗处"]
- Hidden operation requirements: [{"evidence_status": "pending_live_walkthrough", "operation": "stair_transition", "prompt_exposure": "forbidden", "requirement_id": "SLR-N08-H01", "trigger_waypoints": ["教堂楼梯", "教堂2到3暗处楼梯"]}, {"evidence_status": "pending_live_walkthrough", "operation": "low_light_navigation", "prompt_exposure": "forbidden", "requirement_id": "SLR-N08-H02", "trigger_waypoints": ["教堂2到3暗处楼梯", "教堂3楼暗处"]}]
- 静态状态: all_segments_certified；难度预标: D3_vertical_or_multi_junction_static
- 指标: length=231.8, turns=50, ascent=11, descent=2, doors=2

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 基督教汇基堂 | primary | -113,-2,-535 | -113,-2,-535 | 0.0 |
| 2 | via | evaluator_hidden | 教堂楼梯 | primary | -114,-2,-544 | -114,-2,-544 | 0.0 |
| 3 | via | evaluator_hidden | 教堂2楼入口 | primary | -114,4,-545 | -114,4,-545 | 0.0 |
| 4 | via | evaluator_hidden | 教堂2到3暗处楼梯 | primary | -114,4,-543 | -114,4,-543 | 0.0 |
| 5 | via | evaluator_hidden | 教堂3楼暗处 | primary | -117,7,-540 | -117,7,-540 | 0.0 |
| 6 | end | prompt | 教堂3楼 | primary | -117,7,-600 | -117,7,-600 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N08-S01 | 基督教汇基堂 -> 教堂楼梯 | certified_static_reference | 24.9 | 23 | diagonal:3,step:4,walk:15 |
| SLR-N08-S02 | 教堂楼梯 -> 教堂2楼入口 | certified_static_reference | 14.2 | 12 | diagonal:2,step:5,walk:4 |
| SLR-N08-S03 | 教堂2楼入口 -> 教堂2到3暗处楼梯 | certified_static_reference | 1.0 | 2 | walk:1 |
| SLR-N08-S04 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 | 123 | diagonal:16,step:2,walk:104 |
| SLR-N08-S05 | 教堂3楼暗处 -> 教堂3楼 | certified_static_reference | 61.9 | 60 | diagonal:7,walk:52 |

## SLR-N09 · 进入教堂去二楼活动区
- 城市类型: religious entrance to indoor lower floor
- 场景组合: 教堂入口、室内垂直通道、二楼活动区
- 操作重点: 室外到室内转换、垂直移动、二楼到达
- Agent 可见意图: 从基督教汇基堂入口进入，前往二楼活动区。
- Agent 可见点: ["基督教汇基堂", "教堂2楼平台"]
- Evaluator hidden 点: ["教堂楼梯", "教堂2楼入口"]
- Hidden operation requirements: [{"evidence_status": "pending_live_walkthrough", "operation": "stair_transition", "prompt_exposure": "forbidden", "requirement_id": "SLR-N09-H01", "trigger_waypoints": ["教堂楼梯"]}]
- 静态状态: all_segments_certified；难度预标: D2_medium_estate_static
- 指标: length=61.5, turns=22, ascent=8, descent=2, doors=2

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 基督教汇基堂 | connector | -113,-2,-535 | -113,-2,-535 | 0.0 |
| 2 | via | evaluator_hidden | 教堂楼梯 | connector | -114,-2,-544 | -114,-2,-544 | 0.0 |
| 3 | via | evaluator_hidden | 教堂2楼入口 | connector | -114,4,-545 | -114,4,-545 | 0.0 |
| 4 | end | prompt | 教堂2楼平台 | primary | -113,4,-568 | -113,4,-568 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N09-S01 | 基督教汇基堂 -> 教堂楼梯 | certified_static_reference | 24.9 | 23 | diagonal:3,step:4,walk:15 |
| SLR-N09-S02 | 教堂楼梯 -> 教堂2楼入口 | certified_static_reference | 14.2 | 12 | diagonal:2,step:5,walk:4 |
| SLR-N09-S03 | 教堂2楼入口 -> 教堂2楼平台 | certified_static_reference | 22.4 | 23 | diagonal:1,walk:21 |

## SLR-N10 · 从图书馆回到六楼活动区
- 城市类型: indoor upper-floor library errand
- 场景组合: 图书馆、室内短距通道、教堂六楼
- 操作重点: 图书馆起点、室内通行、高层终点确认
- Agent 可见意图: 从图书馆出来，返回教堂六楼活动区。
- Agent 可见点: ["图书馆", "教堂6楼"]
- Evaluator hidden 点: ["需要蹲下的门"]
- Hidden operation requirements: [{"evidence_status": "pending_live_walkthrough", "operation": "sneak", "prompt_exposure": "forbidden", "requirement_id": "SLR-N10-H01", "trigger_waypoints": ["需要蹲下的门"]}]
- 静态状态: all_segments_certified；难度预标: D1_short_simple_static
- 指标: length=10.7, turns=4, ascent=1, descent=0, doors=0

| # | role | visibility | waypoint | coverage | original xyz | tested xyz | snap |
|---:|---|---|---|---|---:|---:|---:|
| 1 | start | prompt | 图书馆 | primary | -108,21,-594 | -108,21,-594 | 0.0 |
| 2 | via | evaluator_hidden | 需要蹲下的门 | primary | -110,21,-594 | -110,21,-594 | 0.0 |
| 3 | end | prompt | 教堂6楼 | primary | -116,22,-601 | -116,22,-601 | 0.0 |

| segment | from -> to | status | length | cells | movement |
|---|---|---|---:|---:|---|
| SLR-N10-S01 | 图书馆 -> 需要蹲下的门 | certified_static_reference | 1.0 | 2 | walk:1 |
| SLR-N10-S02 | 需要蹲下的门 -> 教堂6楼 | certified_static_reference | 9.7 | 9 | diagonal:3,step:1,walk:4 |
