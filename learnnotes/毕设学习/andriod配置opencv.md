###第一步
选择file->new->import module 导入刚刚解压的opencv-3.4.0-android-sdk，选择OpenCV-android-sdk\sdk\java，如下图所示，此时能够看到OpenCVLibrary340被导入进来，然后next->finish即可。导入后，我们的project目录下有一个OpenCVLibrary340的目录。
(注意一定是选中java文件夹)

###第二步
把opencv中的build.gradle和app中的build.gradle的minSdkVersion，targetSdkVersion,compileSdkVersion改为一致

###第三步
在project中添加依赖，File->project structure->app->denpendencies->+->module denpendences

###第四步
把opencv-3.4.0-android-sdk\OpenCV-android-sdk\sdk\native\libs目录下的库复制到我们的project的app\libs目录下

###第五步
在 app （别搞错了）的gradle.build里配置引用刚刚复制进来的库，即把下面的代码添加到gradle.build文件里的android结点下：

<font size=5>

```
sourceSets {
        main {
            jni.srcDirs = []
            jniLibs.srcDirs = ['libs']
        }
    }
```
</font>


###错误: 程序包android.hardware.camera2不存在
检查项目结构中的设置Ctrl +Alt+Shift+s,选择opencvlibrary将compile sdk version改为和app中的compile sdk version一致 
