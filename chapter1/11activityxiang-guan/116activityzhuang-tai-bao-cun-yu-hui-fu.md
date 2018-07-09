#### Activity状态保存于恢复

1、onSaveInstanceState\(\)

* 屏幕旋转重建会调用onSaveInstanceState\(\)
* 启动另一个activity当前activity在离开前会调用onSaveInstanceState\(\)
* 按Home键的情形和启动另一个activity一样, 当前activity在离开前会onSaveInstanceState\(\)

  


2、onRestoreInstanceState\(\):

* 屏幕旋转重建会调用onRestoreInstanceState\(\)
* 启动另一个activity，返回时如果因为被系统杀死需要重建, 则会从onCreate\(\)重新开始生命周期, 调用onRestoreInstanceState\(\)
* 按Home键的情形和启动另一个activity一样，用户再次点击应用图标返回时,
  如果重建发生, 则会调用onCreate\(\)和onRestoreInstanceState\(\)



