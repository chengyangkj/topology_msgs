# topology_msgs

ROS2消息包，用于传递拓扑地图信息。

## 消息类型

### TopologyMapPointInfo.msg
定义拓扑地图中的点信息：
- `name`: 点的名称
- `x`, `y`: 点的坐标
- `theta`: 点的朝向角度
- `type`: 点的类型（如"NavGoal"）

### MapProperty.msg
定义地图属性：
- `support_controllers`: 支持的控制器列表

### RouteInfo.msg
定义路由信息：
- `controller`: 控制器类型

### RouteConnection.msg
定义路由映射：
- `source_point`: 起始点名称
- `target_point`: 目标点名称
- `route_info`: 路由信息

### TopologyMap.msg
完整的拓扑地图结构：
- `map_name`: 地图名称
- `map_property`: 地图属性
- `points`: 点信息数组
- `routes`: 路由映射数组

## 构建

```bash
colcon build --packages-select topology_msgs
```

## 使用示例

这个包可以用于传递类似以下JSON结构的拓扑地图信息：

```json
{
  "map_name": "",
  "map_property": {
    "support_controllers": ["FollowPath", "Backward", "MPPI"]
  },
  "points": [
    {
      "name": "NAV_POINT_0",
      "theta": 0.0,
      "type": "NavGoal",
      "x": -2.901314800901578,
      "y": 3.1583846731780643
    }
  ],
  "routes": [
    {
      "source_point": "NAV_POINT_0",
      "target_point": "NAV_POINT_1",
      "route_info": {
        "controller": "FollowPath"
      }
    }
  ]
}
``` 