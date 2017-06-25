```java
public void invalidate() {
    invalidate(true);
}
void invalidate(boolean invalidateCache) {
  invalidateInternal(0, 0, mRight - mLeft, mBottom - mTop, invalidateCache, true);
}
```
invalidateCache 如果是 true View 缓存失效 <br>
