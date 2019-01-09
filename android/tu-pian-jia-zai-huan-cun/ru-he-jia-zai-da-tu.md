#### 如何加载大图Bitmap

##### 一、通过压缩图片的方法

BitmapFactory 提供了多个解析创建Bitmap;

1. decodeFile

2. decodeStream

3. decodeResource

> 每一种解析方法都提供了一个可选的BitmapFactory.Options参数



参数一、inJustDecodeBounds：获得Bitmap宽高等信息

inJustDecodeBounds属性设置为true就可以让解析方法禁止为bitmap分配内存，返回值也不再是一个Bitmap对象，而是null。虽然Bitmap是null了，但是BitmapFactory.Options的outWidth、outHeight和outMimeType属性都会被赋值。这个技巧让我们可以在加载图片之前就获取到图片的长宽值和MIME类型，从而根据情况对图片进行压缩

```java
BitmapFactory.Options options = new BitmapFactory.Options();
options.inJustDecodeBounds = true;
BitmapFactory.decodeResource(getResources(), R.id.myimage, options);
int imageHeight = options.outHeight;
int imageWidth = options.outWidth;
String imageType = options.outMimeType;
```

参数二、inSampleSize：压缩图片

通过设置BitmapFactory.Options中inSampleSize的值就可以实现。比如我们有一张2048\*1536像素的图片，将inSampleSize的值设置为4，就可以把这张图片压缩成512\*384像素。原本加载这张图片需要占用13M的内存，压缩后就只需要占用0.75M了\(假设图片是ARGB\_8888类型，即每个像素点占用4个字节\)

```java
public static int calculateInSampleSize(BitmapFactory.Options options,
		int reqWidth, int reqHeight) {
	// 源图片的高度和宽度
	final int height = options.outHeight;
	final int width = options.outWidth;
	int inSampleSize = 1;
	if (height > reqHeight || width > reqWidth) {
		// 计算出实际宽高和目标宽高的比率
		final int heightRatio = Math.round((float) height / (float) reqHeight);
		final int widthRatio = Math.round((float) width / (float) reqWidth);
		// 选择宽和高中最小的比率作为inSampleSize的值，这样可以保证最终图片的宽和高
		// 一定都会大于等于目标的宽和高。
		inSampleSize = heightRatio < widthRatio ? heightRatio : widthRatio;
	}
	return inSampleSize;
}

```

具体步骤：

1. BitmapFactory.Options的inJustDecodeBounds属性设置为true，解析一次图片 获得宽高等信息

2. BitmapFactory.Options 和 期望的宽高  ，通过calculateInSampleSize方法得到合适的inSampleSize值

3. 再解析一次图片，使用新获取到的inSampleSize值，并把inJustDecodeBounds设置为false，就可以得到压缩后的图片了

```java
public static Bitmap decodeSampledBitmapFromResource(Resources res, int resId,
        int reqWidth, int reqHeight) {
	// 第一次解析将inJustDecodeBounds设置为true，来获取图片大小
    final BitmapFactory.Options options = new BitmapFactory.Options();
    options.inJustDecodeBounds = true;
    BitmapFactory.decodeResource(res, resId, options);
    // 调用上面定义的方法计算inSampleSize值
    options.inSampleSize = calculateInSampleSize(options, reqWidth, reqHeight);
    // 使用获取到的inSampleSize值再次解析图片
    options.inJustDecodeBounds = false;
    return BitmapFactory.decodeResource(res, resId, options);
}
```





#### 二、图片区域显示

BitmapRegionDecoder：

主要用于显示图片的某一块矩形区域，如果你需要显示某个图片的指定区域，那么这个类非常合适。

```java
InputStream inputStream = getAssets().open("tangyan.jpg");

//获得图片的宽、高
BitmapFactory.Options tmpOptions = new BitmapFactory.Options();
tmpOptions.inJustDecodeBounds = true;
BitmapFactory.decodeStream(inputStream, null, tmpOptions);
int width = tmpOptions.outWidth;
int height = tmpOptions.outHeight;

//设置显示图片的中心区域
BitmapRegionDecoder bitmapRegionDecoder = BitmapRegionDecoder.newInstance(inputStream, false);
BitmapFactory.Options options = new BitmapFactory.Options();
options.inPreferredConfig = Bitmap.Config.RGB_565;
Bitmap bitmap = bitmapRegionDecoder
            .decodeRegion(new Rect(width / 2 - 100, height / 2 - 100, width / 2 + 100, height / 2 + 100), options);
mImageView.setImageBitmap(bitmap);

```











