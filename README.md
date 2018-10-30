# 联通智慧选址大作业
## 数据表信息
**grid位置网格表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| uid | 位置网格编号 | bigint | 网格id |
| centroid_lat | 中心点纬度 | 用于与wgs84表换算 |
| centroid_lon | 中心点经度 | 用于与wgs84表换算 |


**wgs84网格表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| fnid | 位置网格编号 | bigint | 网格id |
| gcol_4326 | 中心点经度 | 标准网格中的位置 |
| grow_4326 | 中心点纬度 | 标准网格中的位置 |
| city_code | 城市id | string | 默认北京V0110000 |

**stay_month月驻留表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| uid | 用户编号 | bigint | 用户id |
| stime | 驻留开始时间 | timestamp | 驻留开始时间 |
| etime | 驻留结束时间 | timestamp | 驻留结束时间 |
| grid_id | 位置网格编号 | bigint | grid表外键 |
| poi_id | 位置点编号 | int | 位置点id <font color=#00ffff>（待确定）</font> |
| ptype | 驻留类型 | int | 0-到访1-居住2-工作 |
| zone_id | 所属区县 | string | 区县id外键 |
| is_core | 是否核心用户 | string | Y/N |

**stay_poi驻留月度表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| uid | 用户编号 | bigint | 用户id |
| poi_id | 位置点编号 | int | 位置点id <font color=#00ffff>（待确定）</font> |
| ptype | 位置点类型 | int | 位置点类型 |
| final_grid_id | 位置网格编号 | bigint | grid外键 |
| stay_fre | 驻留频次 | int | 驻留次数（月记） |
| weighted_centroid_lat | 加权质心纬度 | double | 用于对应wgs84中位置 |
| weighted_centroid_lon | 加权质心经度 | double | 用于对应wgs84中位置 |
| weekday_day_time | 工作日白天停留时长 | BIGINT |  |
| weekday_eve_time | 周末白天停留时长 | BIGINT |  |
| weekend_day_time | 周末白天停留时长 | BIGINT |  |
| weekend_eve_time | 周末夜晚停留时长 | BIGINT |  |
| zone_id | 所属区县编号 | string | 区县id外键 |
| is_core | 是否核心用户 | string | Y/N |

**route_node道路节点表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| rn_id | 道路结点编号 | bigint | |
| lat | 纬度 | 用于与wgs84表换算 |
| lon | 经度 | 用于与wgs84表换算 |
| is_high | 是否道路关键节点 | 是否重要道路节点（决定方向） |

**move_month月出行表**

| 字段id | 字段名称 | 类型 | 含义 |
| ------ | ------ | ------ | ------ |
| uid | 用户ID | bigint | |
| move_id | 中心点纬度 | 用于与wgs84表换算 |
| stime | 出行开始时间 | 用于与wgs84表换算 |
| etime | 出行结束时间 | bigint | |
| mode | 交通方式 | smallint | 1-公路2-铁路3-飞机4-地铁0-其他 |
| start_grid_id | 出行起始位置网格 | bigint | grid表外键 |
| end_grid_id | 出行终止位置网格 | bigint | grid表外键 |
| distance | 速度（km/h） | bigint | |
| speed | 速度（km/h） | int | |
| time | 时长（秒） | bigint | |
| is_core | 是否核心 | string | Y/N |
| end_zone | 终点所属区县 | string | |
| start_zone | 起点所属区县 | string | |
| start_ptype | 起点驻留类型 | int | <font color=#00ffff>（待确定）</font> |
| end_ptype | 终点驻留类型 | int | <font color=#00ffff>（待确定）</font> |