## Espresso

> Espresso是一个Android UI测试框架，由三部分组成

### 添加加依赖库

#### build.gradle(Module)
https://github.com/MAIMIHO/AndroidTest/blob/master/build.gradle
#### build.gradle(app)
https://github.com/MAIMIHO/AndroidTest/blob/master/app/build.gradle
   
### 主要组件

- ViewMachers：寻找View, 定位一个视图
- ViewActions: 执行交互事件. 可以作为参数传入 ​ViewInteraction.perform()​ 方法中的 ViewAction 的集合（如 ​click()）。
- ViewAssertions：检验测试结果, 可以作为参数传入 ​ViewInteraction.check()​ 方法中的 ViewAssertion 的集合。通常，你会使用带有视图匹配器的匹配断言来判断当前被选中视图的状态。

#### 例如:
    onView(withId(R.id.my_view))      // withId(R.id.my_view) is a ViewMatcher
          .perform(click())               // click() is a ViewAction
          .check(matches(isDisplayed())); // matches(isDisplayed()) is a ViewAssertion

#### 查找视图
> 使用 hamcrest 匹配器以期望在当前视图结构里匹配一个（唯一的）视图。


- onView
    - allOf 组合匹配 如: onView(allOf(withId(R.id.my_view), withText("Hello!")))
    - not 反转匹配 如: onView(allOf(withId(R.id.my_view), not(withText("Unwanted"))))
- onData AdapterView建议使用onData

        onView(withId(R.id.spinner_simple)).perform(click());//点击 Spinner
        onData(allOf(is(instanceOf(String.class)), is("Americano"))).perform(click());//点击 “Americano” 条目
        //验证 TextView​ 包含 “Americano” 字符串
        onView(withId(R.id.spinnertext_simple).check(matches(withText(containsString("Americano"))));

- 异常
    - NoMatchingViewException ​onView​ 没有找到目标视图
    - AmbiguousViewMatcherException 给出的匹配器找到了多个视图


#### ViewAction
- perform在视图上执行操作
    - 单个操作 onView(…).perform(click());
    - 多个操作 onView(…).perform(typeText("Hello"), click());
    - 可滚动视图 操作前先显示 onView(…).perform(scrollTo(), click());
- 检查一个视图是否满足断言
    - onView(…).check(matches(withText("Hello!")));

## 参考资料
- http://www.jianshu.com/nb/2795029 lovexiaov
- https://developer.android.com/topic/libraries/testing-support-library/index.html android-testing-support-library/
- https://github.com/googlesamples/android-testing/ android-testing
- https://developer.android.com/training/testing/ui-testing/espresso-testing.html 
- https://developer.android.com/topic/libraries/testing-support-library/index.html
