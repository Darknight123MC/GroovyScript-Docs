# 创建自定义方块

## 简单的方法

````groovy
content.createBlock(String name).register()
````

很简单, 对吧.  
让我们来逐步分解以下这个函数:

- `content`是一个全局变量.
- `createBlock(String name)` 创建一个方块和他的物品形式, 并且返回他本身, name是注册名, 只能由小写字母和下划线`_`组成.  
- `register()` 注册方块和物品.

## 注册方块
上面的例子告诉了你如何创建一个简单的方块, 你也可以自己注册一个方块(以创建自定义事件). 
使用以下函数来注册自定义块:  
````groovy
content.registerBlock(String name, Block block)
content.registerBlock(String name, Block block, ItemBlock block)
````

## 纹理与贴图

Minecraft的方块需要至少一个贴图作为主贴图(即所有面都渲染相同的贴图), 一个设置如何渲染该贴图的模型文件和一个方块状态(BlockState)文件, 该文件将每个方块状态指向一个模型文件.  
如果GrS找不到模型文件或方块状态文件, 就会生成一份默认的文件:  
在`.minecraft/groovy/assets/[pack id]/models/block/[block name].json`和`.minecraft/groovy/assets/[pack id]/blockstates/[item name].json`.  
你必须提供一个贴图才能保证正常的渲染:  
请放置于`.minecraft/groovy/assets/[pack id]/textures/blocks/[block name].png`.  

## 本地化
默认情况下, 游戏内方块物品的名称将会是`tile.[pack id].[block name].name`(未本地化名/Language Key). 如果需要更改它, 请将该名称(未本地化名/Language Key)写入Language文件内.  
GroovyScript将生成一个默认的英文语言文件于`.minecraft/groovy/assets/[pack id]/lang/en_us.lang`.  
如果需要中文翻译, 请在同一目录下创建`zh_cn.lang`文件, 并且将`en_us.lang`的内容进行复制.  

### 实例
首先创建一个方块:
````groovy
content.createBlock('dust_block')
````
让我们假设包的id是`nomifactory`, 所以项目和块的id将是`nomifactory:dust_block`.  
````mclang
tile.nomifactory.dust_block.name=Heart of the universe
````  

`tile.nomifactory.dust_block.name`是默认生成的LangKey. 你可以改成你想要的任何东西.  
最后, 在`.minecraft/groovy/assets/nomifactory/textures/items/dust_block.png`放一张贴图.
