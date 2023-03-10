# pyeconfiguration

简易配置对象, 配置文件导入和保存.



## 安装

使用 pip 安装 econfiguration

`pip install econfiguration`



## 快速上手

```Python
import econfiguration

# 创建一个配置对象
config = econfiguration.Configuration()

# 使用对象属性创建配置条目
config.attr_value = 1

# 使用 key 创建配置条目
config['item_value'] = 2

# 使用对象属性访问配置条目
print(config.attr_value)
print(config.item_value)

# 使用 item 访问配置条目
print(config['attr_value'])
print(config['item_value'])
```


### 嵌套

```Python
import econfiguration

# 创建配置对象
config = econfiguration.Configuration()

# 嵌套配置对象
config.abc = econfiguration.Configuration()

# 设置配置条目
config.abc.value = 1
```


### 导入和保存文件

```Python
import econfiguration

# 在初始化时导入配置文件
config = econfiguration.Configuration('config.json', _type='json')

# 清除所有数据
config._con_clear_data()

# 从 json 文件中更新数据
config._con_update_from_json('config.json')

# 保存配置文件
config._con_asve_as_json('config.json')
```



## Configuration 配置对象

```Python
Configuration(_file: Union[str, list, tuple] = ...,
              _type: str = 'json', read_only: bool = False)
# 创建配置对象
# _file: 需要导入的配置文件路径
# _type: 文件类型 ( 目前只接受 json )
# read_only: 设定这个对象为只读


._con_clear_data() -> None
# 清除所有条目数据

._con_set_read_only(value: bool) -> None
# 设置配置对象为只读模式

._con_is_read_only() -> bool
# 获取配置对象的只读模式描述

._con_update_from_data(data: dict) -> None
# 更新条目数据
# 当某项条目的数据类型为字典且键 ".con_is_configuration" 的值为 True 时将会初始化成一个 Configuration 对象.

._con_update_from_json(_file: Union[str, list, tuple] = ...) -> None
# 从 json 文件中更新数据

._con_get_data() -> dict
# 以字典的形式获取所有条目数据
# 数据类型为 Configuration 的条目也会分解成字典

._con_asve_as_json(_path: Union[str, list, tuple]) -> None
# 保存数据到 json 文件

._con_get_value(__key: str) -> Union[int, float, str, bool, list, tuple, dict]
# 获取指定条目的数据
# 当 key 不存在时返回 None

._con_set_value(__key: str, __value: Union[int, float, str, bool, list, tuple, dict]) -> None
# 设置条目数据
# key 不允许使用 "_con_" 字段开头
# value 不允许使用复杂数据类型
```
