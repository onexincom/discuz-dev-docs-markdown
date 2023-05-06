
# 特殊主题
特殊主题模块用于创建一个特殊主题，特殊主题类型脚本格式

```
<?php

class threadplugin_identifier {

	var $name = 'XX主题';			//主题类型名称
	var $iconfile = 'icon.gif';		//发布主题链接中的前缀图标
	var $buttontext = '发布xx主题';	//发帖时按钮文字

	function newthread($fid) {
		return ...;
	}

	function newthread_submit($fid) {

	}

	function newthread_submit_end($fid, $tid) {

	}

	function editpost($fid, $tid) {
		return ...;
	}

	function editpost_submit($fid, $tid) {

	}

	function editpost_submit_end($fid, $tid) {

	}

	function newreply_submit_end($fid, $tid) {

	}

	function viewthread($tid) {
		return ...;
	}
}

?>
```
### `identifier`
插件的唯一标识符，在插件设置中设置。

### 函数名以及含义
  
  
| **函数名** | **含义** |   
| ---- | ---- |   
| `newthread()` | 发主题时页面新增的表单项目，通过 `return` 返回即可输出到发帖页面中 |   
| `newthread_submit()` | 主题发布后的数据判断 |   
| `newthread_submit_end()` | 主题发布后的数据处理 |   
| `editpost()` | 编辑主题时页面新增的表单项目，通过 `return` 返回即可输出到编辑主题页面中 |   
| `editpost_submit()` | 主题编辑后的数据判断 |   
| `editpost_submit_end()` | 主题编辑后的数据处理 |   
| `newreply_submit_end()` | 回帖后的数据处理 |   
| `viewthread()` | 查看主题时页面新增的内容，通过 `return` 返回即可输出到主题首贴页面中 | 
