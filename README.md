## Espresso

> Espresso是一个Android UI测试框架，由三部分组成

- ViewMachers：寻找View, 定位一个视图
- ViewActions: 执行交互事件. 可以作为参数传入 ​ViewInteraction.perform()​ 方法中的 ViewAction 的集合（如 ​click()）。
- ViewAssertions：检验测试结果, 可以作为参数传入 ​ViewInteraction.check()​ 方法中的 ViewAssertion 的集合。通常，你会使用带有视图匹配器的匹配断言来判断当前被选中视图的状态。


    onView(withId(R.id.my_view))      // withId(R.id.my_view) is a ViewMatcher
          .perform(click())               // click() is a ViewAction
          .check(matches(isDisplayed())); // matches(isDisplayed()) is a ViewAssertion

### 添加加依赖库

    android{
      defaultConfig{
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
      }
    }

    dependencies{
        androidTestCompile 'com.android.support:support-annotations:24.1.1'
        androidTestCompile 'com.android.support.test:runner:0.5'
        androidTestCompile 'com.android.support.test:rules:0.5'
        androidTestCompile 'com.android.support.test.espresso:espresso-core:2.2.2'
        }
## ed