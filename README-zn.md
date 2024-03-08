# 文件介绍
launch 启动入口 -> launch_utils.start -> webui.api_only->api/api
# 调用txt2img ControlNet 


# 重要参数
## shared
shared给我的感觉对应到了UI上能够操作到的所有对象
shared的初始化完成在webui.api_only调用阶段，执行该文件载入的时候执行了initialize.imports()调用了shared_init.initialize()
初始化了shared的主要参数有:
1. state  modules.shared_state
2. opts   modules.options 还有来自于shared_options的(在shared_init的时候发生)
opts在初始化之后还有一个功能与关键字绑定的操作(modules.initialzie : initialize_util.configure_opts_onchange())
在initialize_rest中，shared同时配置了model文件下的所有模型的信息

3. face_restorers 设置为Codeformer  modules.codeformer_model

## scripts
在initialize.initialize的最后调用initialize_rest会执行scripts.load_scripts()从而载入scripts文件夹下的所有scripts和modules.processing_script下的所有script  ，而重启会再次执行initialize_rest，再次载入这几个script的UI
scripts的run()都在这些script文件里！！！


## p txt2imgreq: models.StableDiffusionTxt2ImgProcessingAPI
初始化在 api.api text2imgapi 一开始进行
