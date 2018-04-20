RecyclerView 缓存  
通过三个内部类管理，Recycler、RecycledViewPool,ViewCacheExtension。
主要代码逻辑 见 tryGetViewHolderForPositionByDeadline 方法

主要逻辑在 Recycler，它有 mAttachedScrap ， mChangedScrap ， mCachedViews 三个ArrayList<ViewHolder>来缓存不同状态的 ViewHolder

ViewCacheExtension 是一个抽象类，在 Recycler 的几个缓存中依次查找之后仍没有则会检查 ViewCacheExtension 是否有缓存的  ViewHolder

RecycledViewPool 的逻辑是使用 SparseArray 缓存每个viewType对应的一个ArrayList<ViewHolder> ， Recycler 检查 ViewCacheExtension 之后 会检查这里




mAttachedScrap ， mChangedScrap ， mCachedViews
屏幕内缓存：
  mAttachedScrap  未与RecyclerView分离的ViewHolder
  mChangedScrap   数据已经改变的viewHolder
屏幕外缓存:
  mCachedViews  滑动出屏幕后的缓存 ，大小由 mViewCacheMax 限制 ，超过这个限制 mCachedViews 将 ViewHolder 放入 RecycledViewPool 后移除

ViewCacheExtension 
  开发者自己实现，可以定义一个缓存map将指定viewtype或者position的ViewHolder在 onCreateViewHolder 的时候，或者 RecyclerView 初始化后 ，
  放入缓存，需要设置 recyclerView.setViewCacheExtension(viewCacheExtension)
  
  
RecycledViewPool
  在 RecycledViewPool 的  SparseArray 中， 每种 viewType 对应的 ViewHolder 列表大小限制为 DEFAULT_MAX_SCRAP =5
