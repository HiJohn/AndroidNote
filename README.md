# AndroidNote
Android study note 

![image](http://e.hiphotos.baidu.com/image/pic/item/500fd9f9d72a6059099ccd5a2334349b023bbae5.jpg)
Fragment可以在Activity重新创建时 ,不完全销毁Fragment，以便Fragment可以恢复。在onCreate()方法中调用setRetainInstance(true/false)方法是最佳位置。当Fragment恢复时的生命周期,会跳过onCreate()和onDestroy()方法，因此不能在onCreate()中放置一些初始化逻辑，切忌！
