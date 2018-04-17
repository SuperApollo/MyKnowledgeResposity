# ViewPager 禁止滑动
### 1.利用事件分发机制来控制滑动生效与否
* 设置一个标志位来标记可否滑动
* 根据标志位控制 onInterceptTouchEvent、onTouchEvent 的返回值
* 代码如下
```java     
@Override
    public boolean onInterceptTouchEvent(MotionEvent ev) {
        if (!canScroll) {
            return false;
        }
        return super.onInterceptTouchEvent(ev);
    }

    @Override
    public boolean onTouchEvent(MotionEvent ev) {
        if (!canScroll) {
            return false;
        }
        return super.onTouchEvent(ev);
    }
 ```
### 2.修改 scrollTo 方法来控制滑动生效与否
代码如下
```java
    @Override
    public void scrollTo(int x, int y) {
        if (canScroll)
            super.scrollTo(x, y);
    }
```  
