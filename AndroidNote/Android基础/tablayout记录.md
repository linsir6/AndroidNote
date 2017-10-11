# TabLayout记录

今天用TabLayout的时候发现，TabLayout的setOnPageChangeListener的方法过期了，良好的编程习惯是不在项目中使用过时的方法的，所以要找一个替代的方案：

``addOnPageChangeListener``

- setOnPageChangeListener

```
mViewPager.setOnPageChangeListener(new ViewPager.OnPageChangeListener() {
@Override
public void onPageScrolled(int position, float positionOffset, int positionOffsetPixels) {

}

@Override
public void onPageSelected(int position) {

}

@Override
public void onPageScrollStateChanged(int state) {

}
});
```

- addOnPageChangeListener

```
mViewPager.addOnPageChangeListener(new ViewPager.OnPageChangeListener() {
@Override
public void onPageScrolled(int position, float positionOffset, int positionOffsetPixels) {

}

@Override
public void onPageSelected(int position) {
    selectedTab(position);
}

@Override
public void onPageScrollStateChanged(int state) {

}
});
```
