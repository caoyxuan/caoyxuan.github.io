# Shun Lee 用户标点真实顺序路线
- 来源: `runtime/shun-lee-review-vnc/20260716_clean_v3_shun_lee_review_vnc/local-user-waypoints/shunlee-marked-waypoints.txt`
- World: `eval/snapshots/imported_1_21_1/shun-lee-clean-v3/world`
- 点数: 39；路线数: 10；路段数: 38
- 规则: 严格使用 Xaero waypoint txt 的行顺序切成 10 条连续路线，不按语义、OSM、自然路线重新排序。
- 分段: 相邻路线共享一个边界点；边界点在后一条路线里标记为 connector，避免主点重复计数。
- 边界: waypoint txt 没有连续行走轨迹；两点之间只记录静态寻路状态。

## 可达性概览
- 路线状态: {"marked_route_all_segments_certified": 4, "marked_route_no_static_link": 3, "marked_route_with_static_gaps": 3}
- 路段状态: {"certified_static_reference": 28, "mark_order_large_jump_not_static_tested": 4, "no_path_found": 6}
- 坐标贴近: {"exact_standable": 36, "snapped": 3}

## 10 条路线

### MARKED-01 · 楼群到赛车场
- 点序: #1 到 #6
- 状态: `marked_route_all_segments_certified`；路段: {"certified_static_reference": 5}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 1 | primary | 楼8 | -185,10,-619 | 0.0 |
| 2 | primary | 楼7 | -196,10,-657 | 0.0 |
| 3 | primary | 楼6 | -211,10,-696 | 0.0 |
| 4 | primary | 顺利消防宿舍楼5 | -248,10,-673 | 0.0 |
| 5 | primary | 顺利消防宿舍区入口 | -267,10,-549 | 0.0 |
| 6 | primary | 赛车场 | -147,6,-519 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S01 | 楼8 -> 楼7 | certified_static_reference | 46.2 blocks |
| MARKED-S02 | 楼7 -> 楼6 | certified_static_reference | 44.8 blocks |
| MARKED-S03 | 楼6 -> 顺利消防宿舍楼5 | certified_static_reference | 46.9 blocks |
| MARKED-S04 | 顺利消防宿舍楼5 -> 顺利消防宿舍区入口 | certified_static_reference | 131.3 blocks |
| MARKED-S05 | 顺利消防宿舍区入口 -> 赛车场 | certified_static_reference | 142.3 blocks |

### MARKED-02 · 赛车场到学校片区跳转
- 点序: #6 到 #8
- 状态: `marked_route_no_static_link`；路段: {"mark_order_large_jump_not_static_tested": 2}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 6 | connector | 赛车场 | -147,6,-519 | 0.0 |
| 7 | primary | 健身游乐场 | -15,-2,-651 | 0.0 |
| 8 | primary | 盛德学校篮球场 | -206,-2,-550 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S06 | 赛车场 -> 健身游乐场 | mark_order_large_jump_not_static_tested | 186.7 straight-line blocks |
| MARKED-S07 | 健身游乐场 -> 盛德学校篮球场 | mark_order_large_jump_not_static_tested | 216.1 straight-line blocks |

### MARKED-03 · 学校与教堂外围连续段
- 点序: #8 到 #12
- 状态: `marked_route_all_segments_certified`；路段: {"certified_static_reference": 4}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 8 | connector | 盛德学校篮球场 | -206,-2,-550 | 0.0 |
| 9 | primary | 盛德扶幼中心 | -211,-2,-599 | 0.0 |
| 10 | primary | 羽毛球场 | -92,-2,-573 | 0.0 |
| 11 | primary | 教堂餐厅 | -107,-2,-596 | 0.0 |
| 12 | primary | 迦南書院 | -49,-2,-613 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S08 | 盛德学校篮球场 -> 盛德扶幼中心 | certified_static_reference | 112.6 blocks |
| MARKED-S09 | 盛德扶幼中心 -> 羽毛球场 | certified_static_reference | 148.6 blocks |
| MARKED-S10 | 羽毛球场 -> 教堂餐厅 | certified_static_reference | 29.0 blocks |
| MARKED-S11 | 教堂餐厅 -> 迦南書院 | certified_static_reference | 79.3 blocks |

### MARKED-04 · 迦南书院到教堂六楼入口
- 点序: #12 到 #16
- 状态: `marked_route_with_static_gaps`；路段: {"certified_static_reference": 3, "no_path_found": 1}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 12 | connector | 迦南書院 | -49,-2,-613 | 0.0 |
| 13 | primary | 图书馆 | -108,21,-594 | 0.0 |
| 14 | primary | 需要蹲下的门 | -110,21,-594 | 0.0 |
| 15 | primary | 教堂6楼平台入口 | -113,22,-594 | 1.0 |
| 16 | primary | 教堂6楼 | -116,22,-601 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S12 | 迦南書院 -> 图书馆 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S13 | 图书馆 -> 需要蹲下的门 | certified_static_reference | 1.0 blocks |
| MARKED-S14 | 需要蹲下的门 -> 教堂6楼平台入口 | certified_static_reference | 2.4 blocks |
| MARKED-S15 | 教堂6楼平台入口 -> 教堂6楼 | certified_static_reference | 6.8 blocks |

### MARKED-05 · 教堂高层问题段
- 点序: #16 到 #20
- 状态: `marked_route_no_static_link`；路段: {"no_path_found": 4}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 16 | connector | 教堂6楼 | -116,22,-601 | 0.0 |
| 17 | primary | 教堂5楼 | -117,19,-601 | 0.0 |
| 18 | primary | 为什么这里卡住了 | -112,14,-540 | 0.0 |
| 19 | primary | 教堂4楼暗处 | -114,13,-544 | 1.0 |
| 20 | primary | 教堂2到3暗处楼梯 | -114,4,-543 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S16 | 教堂6楼 -> 教堂5楼 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S17 | 教堂5楼 -> 为什么这里卡住了 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S18 | 为什么这里卡住了 -> 教堂4楼暗处 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S19 | 教堂4楼暗处 -> 教堂2到3暗处楼梯 | no_path_found | no_path_found_under_static_walkability_model |

### MARKED-06 · 教堂暗楼梯到二楼平台
- 点序: #20 到 #24
- 状态: `marked_route_all_segments_certified`；路段: {"certified_static_reference": 4}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 20 | connector | 教堂2到3暗处楼梯 | -114,4,-543 | 0.0 |
| 21 | primary | 教堂3楼暗处 | -117,7,-540 | 0.0 |
| 22 | primary | 教堂3楼 | -117,7,-600 | 0.0 |
| 23 | primary | 教堂楼梯2 | -121,-2,-597 | 0.0 |
| 24 | primary | 教堂2楼平台 | -113,4,-568 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S20 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 blocks |
| MARKED-S21 | 教堂3楼暗处 -> 教堂3楼 | certified_static_reference | 61.9 blocks |
| MARKED-S22 | 教堂3楼 -> 教堂楼梯2 | certified_static_reference | 28.0 blocks |
| MARKED-S23 | 教堂楼梯2 -> 教堂2楼平台 | certified_static_reference | 44.6 blocks |

### MARKED-07 · 教堂低层出口到东侧暗区
- 点序: #24 到 #28
- 状态: `marked_route_with_static_gaps`；路段: {"certified_static_reference": 3, "mark_order_large_jump_not_static_tested": 1}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 24 | connector | 教堂2楼平台 | -113,4,-568 | 0.0 |
| 25 | primary | 教堂2楼入口 | -114,4,-545 | 0.0 |
| 26 | primary | 教堂楼梯 | -114,-2,-544 | 0.0 |
| 27 | primary | 基督教汇基堂 | -113,-2,-535 | 0.0 |
| 28 | primary | 黑暗的地方 | 16,-2,-593 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S24 | 教堂2楼平台 -> 教堂2楼入口 | certified_static_reference | 22.0 blocks |
| MARKED-S25 | 教堂2楼入口 -> 教堂楼梯 | certified_static_reference | 14.9 blocks |
| MARKED-S26 | 教堂楼梯 -> 基督教汇基堂 | certified_static_reference | 24.5 blocks |
| MARKED-S27 | 基督教汇基堂 -> 黑暗的地方 | mark_order_large_jump_not_static_tested | 141.4 straight-line blocks |

### MARKED-08 · 黑暗区到消防/足球场
- 点序: #28 到 #34
- 状态: `marked_route_all_segments_certified`；路段: {"certified_static_reference": 6}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 28 | connector | 黑暗的地方 | 16,-2,-593 | 0.0 |
| 29 | primary | 顺利消防局门口 | -90,-3,-623 | 0.0 |
| 30 | primary | 顺利消防局 | -122,-2,-622 | 0.0 |
| 31 | primary | 顺利足球场正门 | -142,-1,-671 | 0.0 |
| 32 | primary | 顺足侧门 | -118,-2,-674 | 0.0 |
| 33 | primary | 顺利邨游乐场五人制足球场 | -137,-1,-694 | 0.0 |
| 34 | primary | 消防公交车站 | -163,-3,-696 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S28 | 黑暗的地方 -> 顺利消防局门口 | certified_static_reference | 159.2 blocks |
| MARKED-S29 | 顺利消防局门口 -> 顺利消防局 | certified_static_reference | 31.4 blocks |
| MARKED-S30 | 顺利消防局 -> 顺利足球场正门 | certified_static_reference | 85.9 blocks |
| MARKED-S31 | 顺利足球场正门 -> 顺足侧门 | certified_static_reference | 25.4 blocks |
| MARKED-S32 | 顺足侧门 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 27.5 blocks |
| MARKED-S33 | 顺利邨游乐场五人制足球场 -> 消防公交车站 | certified_static_reference | 67.4 blocks |

### MARKED-09 · 公交到纪律部队宿舍
- 点序: #34 到 #38
- 状态: `marked_route_with_static_gaps`；路段: {"certified_static_reference": 3, "mark_order_large_jump_not_static_tested": 1}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 34 | connector | 消防公交车站 | -163,-3,-696 | 0.0 |
| 35 | primary | 顺利部队操场 | -280,10,-563 | 0.0 |
| 36 | primary | 顺利部队宿舍1号楼 | -268,10,-574 | 0.0 |
| 37 | primary | 顺利纪律部队2号楼 | -287,10,-618 | 0.0 |
| 38 | primary | 顺利队宿舍3号楼 | -300,10,-664 | 0.0 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S34 | 消防公交车站 -> 顺利部队操场 | mark_order_large_jump_not_static_tested | 177.1 straight-line blocks |
| MARKED-S35 | 顺利部队操场 -> 顺利部队宿舍1号楼 | certified_static_reference | 17.0 blocks |
| MARKED-S36 | 顺利部队宿舍1号楼 -> 顺利纪律部队2号楼 | certified_static_reference | 60.4 blocks |
| MARKED-S37 | 顺利纪律部队2号楼 -> 顺利队宿舍3号楼 | certified_static_reference | 50.0 blocks |

### MARKED-10 · 纪律宿舍远端
- 点序: #38 到 #39
- 状态: `marked_route_no_static_link`；路段: {"no_path_found": 1}

| # | role | waypoint | tested xyz | snap |
|---:|---|---|---:|---:|
| 38 | connector | 顺利队宿舍3号楼 | -300,10,-664 | 0.0 |
| 39 | primary | 顺利纪律宿舍2座 | -270,2,-741 | 3.6 |

| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S38 | 顺利队宿舍3号楼 -> 顺利纪律宿舍2座 | no_path_found | no_path_found_under_static_walkability_model |

## 全量点序
| # | waypoint | original xyz | tested xyz | snap |
|---:|---|---:|---:|---:|
| 1 | 楼8 | -185,10,-619 | -185,10,-619 | 0.0 |
| 2 | 楼7 | -196,10,-657 | -196,10,-657 | 0.0 |
| 3 | 楼6 | -211,10,-696 | -211,10,-696 | 0.0 |
| 4 | 顺利消防宿舍楼5 | -248,10,-673 | -248,10,-673 | 0.0 |
| 5 | 顺利消防宿舍区入口 | -267,10,-549 | -267,10,-549 | 0.0 |
| 6 | 赛车场 | -147,6,-519 | -147,6,-519 | 0.0 |
| 7 | 健身游乐场 | -15,-2,-651 | -15,-2,-651 | 0.0 |
| 8 | 盛德学校篮球场 | -206,-2,-550 | -206,-2,-550 | 0.0 |
| 9 | 盛德扶幼中心 | -211,-2,-599 | -211,-2,-599 | 0.0 |
| 10 | 羽毛球场 | -92,-2,-573 | -92,-2,-573 | 0.0 |
| 11 | 教堂餐厅 | -107,-2,-596 | -107,-2,-596 | 0.0 |
| 12 | 迦南書院 | -49,-2,-613 | -49,-2,-613 | 0.0 |
| 13 | 图书馆 | -108,21,-594 | -108,21,-594 | 0.0 |
| 14 | 需要蹲下的门 | -110,21,-594 | -110,21,-594 | 0.0 |
| 15 | 教堂6楼平台入口 | -113,21,-594 | -113,22,-594 | 1.0 |
| 16 | 教堂6楼 | -116,22,-601 | -116,22,-601 | 0.0 |
| 17 | 教堂5楼 | -117,19,-601 | -117,19,-601 | 0.0 |
| 18 | 为什么这里卡住了 | -112,14,-540 | -112,14,-540 | 0.0 |
| 19 | 教堂4楼暗处 | -114,12,-544 | -114,13,-544 | 1.0 |
| 20 | 教堂2到3暗处楼梯 | -114,4,-543 | -114,4,-543 | 0.0 |
| 21 | 教堂3楼暗处 | -117,7,-540 | -117,7,-540 | 0.0 |
| 22 | 教堂3楼 | -117,7,-600 | -117,7,-600 | 0.0 |
| 23 | 教堂楼梯2 | -121,-2,-597 | -121,-2,-597 | 0.0 |
| 24 | 教堂2楼平台 | -113,4,-568 | -113,4,-568 | 0.0 |
| 25 | 教堂2楼入口 | -114,4,-545 | -114,4,-545 | 0.0 |
| 26 | 教堂楼梯 | -114,-2,-544 | -114,-2,-544 | 0.0 |
| 27 | 基督教汇基堂 | -113,-2,-535 | -113,-2,-535 | 0.0 |
| 28 | 黑暗的地方 | 16,-2,-593 | 16,-2,-593 | 0.0 |
| 29 | 顺利消防局门口 | -90,-3,-623 | -90,-3,-623 | 0.0 |
| 30 | 顺利消防局 | -122,-2,-622 | -122,-2,-622 | 0.0 |
| 31 | 顺利足球场正门 | -142,-1,-671 | -142,-1,-671 | 0.0 |
| 32 | 顺足侧门 | -118,-2,-674 | -118,-2,-674 | 0.0 |
| 33 | 顺利邨游乐场五人制足球场 | -137,-1,-694 | -137,-1,-694 | 0.0 |
| 34 | 消防公交车站 | -163,-3,-696 | -163,-3,-696 | 0.0 |
| 35 | 顺利部队操场 | -280,10,-563 | -280,10,-563 | 0.0 |
| 36 | 顺利部队宿舍1号楼 | -268,10,-574 | -268,10,-574 | 0.0 |
| 37 | 顺利纪律部队2号楼 | -287,10,-618 | -287,10,-618 | 0.0 |
| 38 | 顺利队宿舍3号楼 | -300,10,-664 | -300,10,-664 | 0.0 |
| 39 | 顺利纪律宿舍2座 | -268,2,-744 | -270,2,-741 | 3.6 |

## 全量连续路段检查
| segment | from -> to | status | length / note |
|---|---|---|---|
| MARKED-S01 | 楼8 -> 楼7 | certified_static_reference | 46.2 blocks |
| MARKED-S02 | 楼7 -> 楼6 | certified_static_reference | 44.8 blocks |
| MARKED-S03 | 楼6 -> 顺利消防宿舍楼5 | certified_static_reference | 46.9 blocks |
| MARKED-S04 | 顺利消防宿舍楼5 -> 顺利消防宿舍区入口 | certified_static_reference | 131.3 blocks |
| MARKED-S05 | 顺利消防宿舍区入口 -> 赛车场 | certified_static_reference | 142.3 blocks |
| MARKED-S06 | 赛车场 -> 健身游乐场 | mark_order_large_jump_not_static_tested | 186.7 straight-line blocks |
| MARKED-S07 | 健身游乐场 -> 盛德学校篮球场 | mark_order_large_jump_not_static_tested | 216.1 straight-line blocks |
| MARKED-S08 | 盛德学校篮球场 -> 盛德扶幼中心 | certified_static_reference | 112.6 blocks |
| MARKED-S09 | 盛德扶幼中心 -> 羽毛球场 | certified_static_reference | 148.6 blocks |
| MARKED-S10 | 羽毛球场 -> 教堂餐厅 | certified_static_reference | 29.0 blocks |
| MARKED-S11 | 教堂餐厅 -> 迦南書院 | certified_static_reference | 79.3 blocks |
| MARKED-S12 | 迦南書院 -> 图书馆 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S13 | 图书馆 -> 需要蹲下的门 | certified_static_reference | 1.0 blocks |
| MARKED-S14 | 需要蹲下的门 -> 教堂6楼平台入口 | certified_static_reference | 2.4 blocks |
| MARKED-S15 | 教堂6楼平台入口 -> 教堂6楼 | certified_static_reference | 6.8 blocks |
| MARKED-S16 | 教堂6楼 -> 教堂5楼 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S17 | 教堂5楼 -> 为什么这里卡住了 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S18 | 为什么这里卡住了 -> 教堂4楼暗处 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S19 | 教堂4楼暗处 -> 教堂2到3暗处楼梯 | no_path_found | no_path_found_under_static_walkability_model |
| MARKED-S20 | 教堂2到3暗处楼梯 -> 教堂3楼暗处 | certified_static_reference | 129.8 blocks |
| MARKED-S21 | 教堂3楼暗处 -> 教堂3楼 | certified_static_reference | 61.9 blocks |
| MARKED-S22 | 教堂3楼 -> 教堂楼梯2 | certified_static_reference | 28.0 blocks |
| MARKED-S23 | 教堂楼梯2 -> 教堂2楼平台 | certified_static_reference | 44.6 blocks |
| MARKED-S24 | 教堂2楼平台 -> 教堂2楼入口 | certified_static_reference | 22.0 blocks |
| MARKED-S25 | 教堂2楼入口 -> 教堂楼梯 | certified_static_reference | 14.9 blocks |
| MARKED-S26 | 教堂楼梯 -> 基督教汇基堂 | certified_static_reference | 24.5 blocks |
| MARKED-S27 | 基督教汇基堂 -> 黑暗的地方 | mark_order_large_jump_not_static_tested | 141.4 straight-line blocks |
| MARKED-S28 | 黑暗的地方 -> 顺利消防局门口 | certified_static_reference | 159.2 blocks |
| MARKED-S29 | 顺利消防局门口 -> 顺利消防局 | certified_static_reference | 31.4 blocks |
| MARKED-S30 | 顺利消防局 -> 顺利足球场正门 | certified_static_reference | 85.9 blocks |
| MARKED-S31 | 顺利足球场正门 -> 顺足侧门 | certified_static_reference | 25.4 blocks |
| MARKED-S32 | 顺足侧门 -> 顺利邨游乐场五人制足球场 | certified_static_reference | 27.5 blocks |
| MARKED-S33 | 顺利邨游乐场五人制足球场 -> 消防公交车站 | certified_static_reference | 67.4 blocks |
| MARKED-S34 | 消防公交车站 -> 顺利部队操场 | mark_order_large_jump_not_static_tested | 177.1 straight-line blocks |
| MARKED-S35 | 顺利部队操场 -> 顺利部队宿舍1号楼 | certified_static_reference | 17.0 blocks |
| MARKED-S36 | 顺利部队宿舍1号楼 -> 顺利纪律部队2号楼 | certified_static_reference | 60.4 blocks |
| MARKED-S37 | 顺利纪律部队2号楼 -> 顺利队宿舍3号楼 | certified_static_reference | 50.0 blocks |
| MARKED-S38 | 顺利队宿舍3号楼 -> 顺利纪律宿舍2座 | no_path_found | no_path_found_under_static_walkability_model |
