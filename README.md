# RemoteSync使用说明

### Client端（源数据端）：
* **source.py** : 源数据端主程序

* **appendwrite.py** : 测试模拟源数据文件的动态写入

* **readFile.py** : 追加读取文件，是工具程序

　　在源数据端（windows）运行appendwrite.py,需要提供一个系统参数指定源数据目录路径，以‘/’结尾;
  
　　在源数据端（windows）运行source.py,需要提供3个系统参数：第一个为源数据目录路径，以‘/’结尾；第二个为备份端的ip地址，第三个参数是开始备份日期yyyymmdd。


### Server端（备份端）：
＊　**backup.py** : 备份端主程序

　　在备份端运行backup.py，需要提供一个系统参数指定备份存储目录路径，以‘/’结尾。

## 注意：
1. 先启动备份端的backup.py,后启动源数据端的source.py。
2. 中途备份端意外退出时，如果源数据端没停止，在当天24点前只需重启备份端backup.py。
3. 如果备份端意外退出，迟于当天24点才发现的，如果直接重启备份端，只能从重启当天的0点开始备份；如需补回期间缺失数据，请先停止源数据端source.py,然后将备份端意外退出当天的数据文件删除后，记下崩溃当天的日期yyyymmdd作为source.py的第三个参数，重复步骤1。
