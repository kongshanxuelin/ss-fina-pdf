### 概述
基于**sumatrapdf**二次开发的PDF浏览器，与传统的PDF浏览器相比，该浏览器针对金融类的PDF文档提供诸多额外特色功能。在我们内部，使用它作为数据核验，数据比对，数据发布等。目前我们独立分支开放了该工具下载，与iqb平台协同使用，可以让你查阅金融类文档事半功倍。

### 特色功能
- **印影版PDF版面识别**：财务类或评级报告等经常会碰到影印版PDF，利用此功能，可提供诸多功能：如一键复制图片里的表格到Excel，文本复制等。
![](http://doc.sumslack.com/server/index.php?s=/api/attachment/visitFile&sign=e457238edfe64d3cc319539cb881ec5b)
- **文件模型识别**：如果打开的文档在我们解析模型库里存在，在右侧面板会自动出现结构化解析数据，你可以针对解析字段进行包括定位，复制等操作，方便查看该文档的关键信息。
![](http://doc.sumslack.com/server/index.php?s=/api/attachment/visitFile&sign=bfc277908b3897635e07fe6569a590d7)
- **浏览器里打开工具**：支持在网页中打开该工具，查阅PDF文件内容。
- **相关文档**：点击相关文档按钮，可查看于此相关的文档。
- **文档搜索**：支持语义查询文档中心的文档，非常方便的随时打开您想要看的文件。
- **区域选取OCR**：可通过内置截图工具，截取相关区域进行OCR，提取精度会大大提高。
- **支持标注**：如果您对我们识别的效果不满意，通过表格标注按钮通过标注表格结构反馈给我们，以便我们提高识别准确率。也可以通过+，-号按钮标注其他文档对象，如标题，列表等。
![](http://doc.sumslack.com/server/index.php?s=/api/attachment/visitFile&sign=35a32e507dd509564a2ddc8f94c62f30)

### 功能重写
- 打开：先本地打开文件展现PDF文档后，调用上传接口（异步调用），通过后台接口获取fileid，根据fileid，获取模型解析列表渲染右侧侧边栏，如果没有匹配的模型，无右侧面板。
- 文件菜单后增加：从云文件库中打开，通过搜索文件名找到自己想要的文件后打开。
- 增加全局搜索：输入框后增加一个按钮：高级搜索，直接本地默认浏览器打开：https://iqb.idbhost.com
![](http://doc.sumslack.com/server/index.php?s=/api/attachment/visitFile&sign=7a7985f0d41d44afa84bd072e006f7d4)
- 版面识别后：各个矩形框支持右键操作，加入复制按钮。
- URL Protocol：使用：ss://pdf/?参数列表  协议，打开本地浏览器，技术帖子请参考：https://blog.csdn.net/technologyleader/article/details/125439627
- 工具栏增加“相似文档”按钮：点击后，显示相似文档
- 开放版去除功能：转HTML解析调试，库值，重新解析KV，发布预览，提交数据按钮，修改定位
- 加入字段本地搜索
![](http://doc.sumslack.com/server/index.php?s=/api/attachment/visitFile&sign=dd8a487e137ae981920330602b147f54)

### 整体框架
- 总体框架和PDF的展示及操作, 采用开源的sumatrapdf, 界面使用win32 Api处理事件及绘图, PDF解析采用的mupdf;
- 右侧kv树使用duilib库, 其中的表格控件为自研, 支持合并单元格, 转置, 树形表格, 解析html表格, 撤回(ctrlz)等功能;

