#Invalidate

```java
public void invalidate() {
    invalidate(true);
}
void invalidate(boolean invalidateCache) {
  invalidateInternal(0, 0, mRight - mLeft, mBottom - mTop, invalidateCache, true);
}
```
invalidateCache 如果是 true View 缓存失效 <br>

```java
void invalidateInternal(int l, int t, int r, int b, boolean invalidateCache,
        boolean fullInvalidate) {
    //根据View的标记位来判断该子View是否需要重绘，假如View没有任何变化，那么就不需要重绘
    if ((mPrivateFlags & (PFLAG_DRAWN | PFLAG_HAS_BOUNDS)) == (PFLAG_DRAWN | PFLAG_HAS_BOUNDS)
            || (invalidateCache && (mPrivateFlags & PFLAG_DRAWING_CACHE_VALID) == PFLAG_DRAWING_CACHE_VALID)
            || (mPrivateFlags & PFLAG_INVALIDATED) != PFLAG_INVALIDATED
            || (fullInvalidate && isOpaque() != mLastIsOpaque)) {
        if (fullInvalidate) {
            mLastIsOpaque = isOpaque();
            mPrivateFlags &= ~PFLAG_DRAWN;
        }

        //设置PFLAG_DIRTY标记位
        mPrivateFlags |= PFLAG_DIRTY;

        if (invalidateCache) {
            mPrivateFlags |= PFLAG_INVALIDATED;
            mPrivateFlags &= ~PFLAG_DRAWING_CACHE_VALID;
        }

        // Propagate the damage rectangle to the parent view.
        //把需要重绘的区域传递给父容器
        final AttachInfo ai = mAttachInfo;
        final ViewParent p = mParent;
        if (p != null && ai != null && l < r && t < b) {
            final Rect damage = ai.mTmpInvalRect;
            damage.set(l, t, r, b);
            //调用父容器的方法，向上传递事件
            p.invalidateChild(this, damage);
        }
        ...
    }
}
```
View是否需要重绘，接着为该View设置标记位，然后把需要重绘的区域传递给父容器，即调用父容器的invalidateChild方法 <br>

