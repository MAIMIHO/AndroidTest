## Espresso

> Espresso是一个Android UI测试框架，由三部分组成

- ViewMachers：寻找View
- ViewActions: 执行交互事件
- ViewAssertions：检验测试结果

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