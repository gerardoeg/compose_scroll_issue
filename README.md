# compose_scroll_issue
Basic project to reproduce an error with the scroll mainly on samsung devices.

Reproduced by now in the following devices:
1. SAMSUNG A70 - Android 10
1. Samsung galaxy A22 - android 13
1. Samsung galaxy A71 - android 13
1. ZTE blade A05- android 9


Jetpack Compose version: 2023.08.00, 2023.10.01, 2022.12.00(current on project)

Jetpack Compose component used: OutlinedTextField

Android Studio Build: Android Studio Iguana | 2023.2.1 Canary 7, and CI compiled APK.

Kotlin version: 1.9.0, 1.9.20, 1.7.10 (respectively)

Steps to Reproduce or Code Sample to Reproduce:
1. Install a debug or release version of the minimal reproducible project
2. Disconnect the device from the usb port.
3. Set the focus to one Input from the list.
3. Scroll until scroll stop working smoothly.

How do I create the list:

´´´
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
 
     LazyColumn(
         modifier = modifier
             .fillMaxSize()
             .testTag("lazyColumn")
     ) {
 
         for (i in 0..100) {
 
             item(key = i) {
 
                 Column(modifier = modifier.fillMaxWidth()) {
 
                     val valueText = "valueText $i"
                     val onValueChange: (String) -> Unit = {}
 
                     OutlinedTextField(
                         modifier = Modifier.fillMaxWidth(),
                         value = valueText,
                         onValueChange = onValueChange
                     )
                 }
             }
         }
     }
 }
´´´

Stack trace (if applicable): NA.

Minimal reproducible repo: 
https://github.com/gerardoeg/compose_scroll_issue

Some Looms that might help: 
Jetpack Compose Scroll Issue - problem
https://www.loom.com/share/eb24a064d0a54d68b7c3deebf80ea087

Jetpack Compose Scroll Issue - expected behavior
https://www.loom.com/share/8df5285fb664421e9261252239c667a0


See reported bug on issue tracker
[https://issuetracker.google.com/issues/313971435](https://issuetracker.google.com/issues/313971435)
