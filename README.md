# 简单分布式文件服务器（类fastdfs）在运维管理等方面优于fastdfs

- 支持curl命令上传
- 支持浏览器上传
- 支持HTTP下载
- 支持多机自动同步
- 类fastdfs
- 高性能 （使用leveldb作为kv库）
- 高可靠（设计极其简单，使用成熟组件）

# 优点

- 无依赖(单一文件）
- 自动同步
- 失败自动修复
- 按天分目录方便维护
- 文件自动去重
- 支持浏览器上传
- 运维简单，只有一个角色（不像fastdfs有三个角色Tracker Server,Storage Server,Client），配置自动生成
- 每台机器对等



# 启动服务器（已编译，[下载直接](https://github.com/sjqzhang/FileServer/releases)）

`./fileserver`

# 配置自动生成  (conf/cfg.json)
```json
{
	"绑定端号": "端口",
	"addr": ":8080",
	"集群": "集群列表例如： http://10.1.xx.2:8080,http://10.1.xx.5:8080,http://10.1.xx.60:8080,注意是字符串数组",
	"peers": ["%s"],
	"组号": "组号",
	"group": "group1",
	"refresh_interval": 120,
	"是否自动重命名": "真假",
	"rename_file": false,
	"是否支持web上传": "真假",
	"enable_web_upload": true,
	"是否支持非日期路径": "真假",
	"enable_custom_path": true,
	"下载域名": "dowonload.web.com",
	"download_domain": "",
	"是否显示目录": "真假",
	"show_dir": true
}
```


# 命令上传

`curl -F file=@http-index-fs http://10.1.50.90:8080/upload` 	


# WEB上传（浏览器打开）

`http://127.0.0.1:8080` 	
