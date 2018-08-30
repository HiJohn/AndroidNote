Fragment可以在Activity重新创建时 ,不完全销毁Fragment，以便Fragment可以恢复。  </br>在onCreate()方法中调用setRetainInstance(true/false)方法是最佳位置。  </br>当Fragment恢复时的生命周期,会跳过onCreate()和onDestroy()方法，因此不能在onCreate()中放置一些初始化逻辑！
