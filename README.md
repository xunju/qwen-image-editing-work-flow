# qwen-image-editing-work-flow
## 实现目标
image editting的流水线数据集增强  

输入：一个image文件夹，depth文件夹，label文件夹   
输出：image_editted，depth_editted，label_editted   
其中对于每一张image，都有若干种edit方式，以后缀_{edit_mode}.png表示   
然后把depth、label的对应项复制而不用改变  
edit_mode例如：把桌子颜色换成黄色、把地板换成瓷砖、在地板上新增某某物体、在桌子旁边再放一个桌子等
由于测试集暂时没有深度图,暂时copy图片rgb格式待处理

增强后格式参考:  
```
├── image_edited/
│   ├── 001_table_yellow.png
│   ├── 001_floor_tile.png
│   ├── 001_add_chair.png
├── depth_edited/
│   ├── 001_table_yellow.png
│   ├── 001_floor_tile.png
│   ├── 001_add_chair.png
├── label_edited/
│   ├── 001_table_yellow.txt
│   ├── 001_floor_tile.txt
│   ├── 001_add_chair.txt
```

### 结果
目前可以实现加凳子,改地板,地板放饮料的功能,但是改方桌桌面颜色不稳定(有时候会把这个桌子改成黄色,有时候会改桌面上的物品)

## 代码如何使用
环境放在/opt/local_env/editor  
```bash
conda activate /opt/local_env/editor
```
将模型代码放置在autodl的autodl-tmp文件夹下(需要扩容20GB)运行命令参考:  
```bash
python edit_pipeline.py --modes table_yellow
```
注意:再次测试记得将上次的edit文件夹删除
