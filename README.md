# 多线程下载项目

本项目是一个展示多线程下载的项目，利用线程池(Executors.newFixedThreadPool(2))对线程的管理和断点续传，第一个版本默认可以两个线程同时下载。

效果图

![image](https://github.com/qianxiangsen521/Multi-threadedDownload/blob/master/gif/down.gif)  

![image](https://github.com/qianxiangsen521/Multi-threadedDownload/blob/master/gif/down.png)  

用法
	
   您需要将这些权限包含在您的AndroidManifest.xml文件中

	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>

创建实例及配置

  1.创建DownloadMessage实例

  DownloadMessage downlaod = DownloadMessage.init(this);

  2.参数配置 添加任务 需要一个Task对象。

  Task task1 = new Task();
  task1.setName("任务1");
  task1.setIamgeUrl(Constants.IMG);
  task1.setId(1);
  task1.setmUniquely_id("102");
  task1.setUrl(Constants.URL1);

  2.1第二参数下载回掉默认是ui线程 提供了三个回掉方法

  public void UiStrat()
  开始下载
  public void UiProgress(Task task,long TotalSize ,int downloadSize)
  下载的进度
  public void UiFinish(Task task)
  下载结束

  Task task = downlaod.addTask(task1,DownloadUiListener)

  3. 开始下载 

  downlaod.startDownload(task);

  4.暂停下载

  downlaod.pauseDownload(task);

  5.删除下载
