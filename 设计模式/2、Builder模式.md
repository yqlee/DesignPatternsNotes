## Builder模式 ##
1. Builder模式定义与使用场景：  
  将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。
2. UML类图：  
  ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/设计模式/UML/2、Builder模式.png)  
  Product产品类：产品的抽象类  
  Builder：抽象的Builder类，规范产品的组建，一般由子类实现具体的组建过程  
  ConcreteBuilder：具体的Builder类  
  Director：统一组装过程  
  在开发实现过程中 ，Director角色经常会被省略。而直接使用一个Builder来进行对象的组装，这个Builder通常为链式调用，它的关键点是每个setter方法都返回自身this，这样使得setter方法可以链式调用。
3. Builder模式的源码实现：  
  AlertDialog  
  AlertDialog的Builder模式并没有Director角色的出现。AlertDialog.Builder同时扮演着Builder、ConcreteBuilder、Director的角色。  
4. 实战使用：  
  ImageLoader是一个优秀的图片处理框架，我们可以使用Builder构建ImageLoader的配置对象：  
  <pre><code>
  public static void init(Context context) {
        int memoryCacheSize = (int) (Runtime.getRuntime().maxMemory() / 10);
        File cacheDir = getCacheDirectory(context);
        //使用Builder构建ImageLoader的配置对象
        ImageLoaderConfiguration config = new ImageLoaderConfiguration.Builder(context)
                .memoryCacheExtraOptions(320, 480)
                // max width, max height，即保存的每个缓存文件的最大长宽
                //加载图片的线程数
                .threadPoolSize(5)
                .threadPriority(Thread.NORM_PRIORITY - 1)
                //解码图像的大尺寸，将在内存中缓存先前解码图像的小尺寸
                .denyCacheImageMultipleSizesInMemory()
                .memoryCache(new UsingFreqLimitedMemoryCache(memoryCacheSize))
                .memoryCacheSize(2 * 1024 * 1024)
                .diskCacheSize(30 * 1024 * 1024)
                // 将保存的时候的URI名称用MD5 加密
                .tasksProcessingOrder(QueueProcessingType.LIFO)
                // 缓存的文件数量
                .diskCache(new UnlimitedDiscCache(cacheDir))
                // 自定义缓存路径
                .defaultDisplayImageOptions(DisplayImageOptions.createSimple())
                .imageDownloader(new BaseImageDownloader(context, 5 * 1000, 30 * 1000)) // connectTimeout
                //.writeDebugLogs() 
                //Remove for release app
                .build();
        //使用配置对象初始化ImageLoader
        ImageLoader.getInstance().init(config);
    }
  </code></pre>