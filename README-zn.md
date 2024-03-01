# 文件介绍
launch 启动入口 -> launch_utils.start -> webui.api_only->api/api


# 重要参数
## share 
share的初始化完成在webui.api_only调用阶段，执行该文件载入的时候执行了initialize.imports()调用了shared_init.initialize()
初始化了shared的主要参数有:
1. state  modules.shared_state
2. opts   modules.options
opts在初始化之后还有一个功能与关键字绑定的操作(modules.initialzie : initialize_util.configure_opts_onchange())
