# События о крашах для SDK

События отправляется при крашах приложения. Собираются автоматически. Название/тип ошибки должен передаваться как название события **event\_name = КРЭШ ГРУППА**

Пример:

```
java.lang.RuntimeException
```

| src      | Путь до файла, где возникла ошибка |
| -------- | ---------------------------------- |
| log      | Лог ошибки                         |
| describe | Описание ошибки                    |

Пример: meta=

```
{
    "src":"ru/top100/tracker/app/ui/fragment/FirstFragment",
    "log":"java.lang.RuntimeException",
    "describe":"ru.top100.tracker.app.ui.fragment.FirstFragment.onViewCreated$lambda-20$lambda-19$lambda-18(FirstFragment.kt:98)\nru.top100.tracker.app.ui.fragment.FirstFragment. $r8$lambda
    $lqmFQulFKCgsyZam7q9ek1uumPQ(FirstFragment.kt:0)\nru.top100.tracker.app.ui.fragment.FirstFragment$$ExternalSyntheticLambda9.onClick(R8$$SyntheticClass:0)
    \nandroid.view.View.performClick(View.java:7506)\ncom.google.android.material.button.MaterialButton.performClick(MaterialButton.java:1194)
    \nandroid.view.View.performClickInternal(View.java:7483)\nandroid.view.View.-$$Nest$mperformClickInternal(UnknownSource:0)
    \nandroid.view.View$PerformClick.run(View.java:29334)\nandroid.os.Handler.handleCallback(Handler.java:942)\nandroid.os.Handler.dispatchMessage(
    Handler.java:99)\nandroid.os.Looper.loopOnce(Looper.java:201)\nandroid.os.Looper.loop(Looper.java:288)\nandroid.app.ActivityThread.main
    (ActivityThread.java:7872)\njava.lang.reflect.Method.invoke(NativeMethod)
    \ncom.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:548)\ncom.android.internal.os.ZygoteInit.main(ZygoteInit.java:936)\n"
}
```
