#1、java文件结构及说明
![image](https://github.com/openthos/oto-filemanager/blob/master/doc/summary/pictures/java_structure.png)

|文件名|说明|
|------|----|
|PathAdapter.java|地址栏适配器|
|PersonalAdapter.java|个人空间界面适配器|
|SeafileAdapter.java|云服务界面适配器|
|CompressDialog.java|文件压缩对话框|
|CopyInfoDialog.java|文件复制信息对话框|
|CreateFileDialog.java|文件文件对话框|
|DiskDialog.java|主|
|FrameSelectView.java|框选自定义view|
|GifView.java|动图自定义view|
|MenuFirstDialog.java|主界面右键菜单|
|OpenWithDialog.java|选择打开文件方式对话框|
|PersonalMenuDialog.java|个人空间文件夹右键菜单|
|PropertyDialog.java|文件和文件夹属性菜单|
|SeafileDialog.java|云服务界面右键菜单|
|TextSelectDialog.java|未知类型文件打开时选择文件类型对话框|
|GragGridView.java|网格布局自定义view|
|GragListView.java|列表布局自定义view|
|PersonalSpaceFragment.java|个人空间界面|
|SdStorageFragment.java|默认界面|
|SeafileFragment.java|云服务界面|
|SearchFragment.java|文件搜索界面|
|SystemSpaceFragment.java|展示指定路径所有文件和文件夹的界面|
|RecycleConentProvider.java|主|
|CompressFormatType.java|枚举，包括tar,gzip,bzip2,zip,rar五大类可扩展|
|Constants.java|常量|
|FileInfo.java|文件和文件夹信息bean|
|FileListAdapter.java|展示指定路径文件的适配器|
|FileOperationHelper.java|文件操作工具类|
|FileSortHelter.java|文件排序工具类|
|FileViewInteractionHub.java|文件交互工具类|
|SeafileSQLLiteHelper.java|云服务数据库|
|Util.java|基本工具类|
|BaseActivity.java|主界面父类|
|BaseDialog.java|对话框父类|
|BaseFragment.java|fragment父类|
|MainActivity.java|主界面|

#2、布局文件结构
![image](https://github.com/openthos/oto-filemanager/blob/master/doc/summary/pictures/layout.png)
#3、云服务的接口：
###对应网络文件的三个状态，分别是已同步，没有同步，和加号
     int STATUS_SYNCHRONIZED = 1;
     int STATUS_UNSYNCHRONIZED = 2;
     int STATUS_ADD = -1;

云盘获取网络文件列表显示：
initCloudFile()函数里面获取并且显示文件，调用工程师的list命令，获取服务器的文件列表，每一个文件夹信息赋值给Seafile对象，每一个seafile对象分为已同步和未同步，然后加入到mCloudFiles列表中。然后让mCloudFileAdapter更新。
初始或者网络文件列表更新的时候就调用initCloudFile()。

    添加同步文件夹：选择要同步的文件夹，对应的是DialogPathSelector类，onCreate函数里面调用同步命令

    对已同步的文件解除同步：MenuDialog3类，onClick函数里面case R.id.desync处调用解除同步命令

    对未同步的文件夹下载并同步：MenuDialog4 类，onClick函数里面case R.id.download处调用命令下载并同步
