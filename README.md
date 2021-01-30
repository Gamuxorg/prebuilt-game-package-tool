# prebuilt-game-package-tool

linux中文游戏站准备的打包工具

## 手动构建appimage

下载本工具后，将游戏文件复制到game.AppDir/usr/bin/game内，或将整个游戏目录复制到game.AppDir/usr/bin，然后将游戏目录改名为game

请注意，gog游戏，只需要复制游戏目录下的game目录内的文件即可。请确保只复制包含了游戏文件的父目录即可。

### 配置

- 修改game.AppDir/usr/bin/config配置文件

	- GAMUX_GAME_NAME,游戏英文名，不要带空格、符号和中文
	
	- GAMUX_GAME_EXEC,在game.AppDir/usr/bin/game内的实际执行的游戏二进制文件名或启动脚本名
	
	- GAMUX_STEAMRUNTIME,为0则表示不需要加载steam-runtime，为1表示加载。如果不需要加载，可以考虑删掉steam-runtime目录减少游戏体积
	
	- PLATFORM,多架构支持，暂未实现，可以忽略
	
	- gamux_function1(),如果默认的脚本不能满足打包需求，则进行额外添加，如添加更多环境变量等
		
- 修改game.AppDir/game.desktop

	- Name,游戏中文名
		
- 找一张游戏logo替换默认的game.png,仅支持png、svg两种格式图片

### 打包

```shell
ARCH=x86_64 ./appimagetool-x86_64.AppImage ./game.AppDir 游戏英文名(全小写)_版本号(数字+点组合)_架构.appimage 
```

架构列表：

- i386，表示x86的32位游戏

- amd64，表示x86的64位游戏

- armhf，表示arm的硬浮点32位游戏

- arm64，表示arm的64位游戏

例如

```shell
ARCH=x86_64 ./appimagetool-x86_64.AppImage ./game.AppDir openttd_1.20153.8.01_amd64.appimage 
```

## 图形化打包

暂未实现，开发中
