## Tutorial 5

### Reflection

Jmeter Results before Profiling
![jm1](https://media.discordapp.net/attachments/1054028087551078452/1217153844937625640/image.png?ex=6602fdda&is=65f088da&hm=0ca49ce965c633c26b8ad48eebcb2d22b96b43e0689e229ebaa77a73d8f71bbf&=&format=webp&quality=lossless&width=687&height=387)
![jm2](https://media.discordapp.net/attachments/1054028087551078452/1217155086858453082/image.png?ex=6602ff02&is=65f08a02&hm=f940c3fe922279b0d286f2da1b314eafac7b9159f85820110ffedb4aa9c6da59&=&format=webp&quality=lossless&width=1038&height=585)
![jm3](https://media.discordapp.net/attachments/1054028087551078452/1217154857794928732/image.png?ex=6602fecb&is=65f089cb&hm=5273877baefa4798d9d2c24791aa84a6eb6070a0a4a21d3a715b66d74b9b1372&=&format=webp&quality=lossless&width=1038&height=585)

JMeter Results CLI
![cli1](https://media.discordapp.net/attachments/1054028087551078452/1217156801536200815/image.png?ex=6603009b&is=65f08b9b&hm=184f03b8148c29349c363b5105fb646a7f2c3105bd361c06818758fbd194a0f2&=&format=webp&quality=lossless&width=1196&height=250)
![cli2](https://media.discordapp.net/attachments/1054028087551078452/1217157110119399545/image.png?ex=660300e4&is=65f08be4&hm=799b51663d23c10c82779e9248b6b291f5d567cc0b17a83fbb8d25ca59dc81e2&=&format=webp&quality=lossless&width=1196&height=226)
![cli3](https://media.discordapp.net/attachments/1054028087551078452/1217157338872676483/image.png?ex=6603011b&is=65f08c1b&hm=e46c39b22f01c79d7afbf803e0c8b30effa69f12946e33560971f2ac6d4580f6&=&format=webp&quality=lossless&width=1196&height=241)

JMeter Results after profiling
![cli1a](https://media.discordapp.net/attachments/1054028087551078452/1217165456503476244/image.png?ex=660308aa&is=65f093aa&hm=5eabf46c014107505a6d0132ad1e25a74f7df66ea6f160a39e6b2fbe7df00792&=&format=webp&quality=lossless&width=1196&height=243)
![cli2a](https://media.discordapp.net/attachments/1054028087551078452/1217165510269997136/image.png?ex=660308b7&is=65f093b7&hm=f9cc65a09cedc0f6aa0d44fe90bf9ea45a2089f42a994776d3953e417a514683&=&format=webp&quality=lossless&width=1196&height=368)
![cli3a](https://media.discordapp.net/attachments/1054028087551078452/1217165456503476244/image.png?ex=660308aa&is=65f093aa&hm=5eabf46c014107505a6d0132ad1e25a74f7df66ea6f160a39e6b2fbe7df00792&=&format=webp&quality=lossless&width=1196&height=243)

When comparing the difference between the results of JMeter before and after profiling, the speed of executing requests in both implementations is significantly different. This is particularly noticeable in the implementation of `getAllStudentCourses`, which initially took around 80000 milliseconds and reduced to 4000 milliseconds. A similar effect is seen in the refactoring of `joinStudentName`, which affected the processing time of requests on the `/all-student-name` endpoint, reducing it to 1/75 of its original time during testing. Refactoring `findStudentWithHighestGPA` also accelerated the processing of requests to the `/highest-gpa` endpoint. The conclusion drawn is that optimizations made to internal parts of the application, such as the program itself, also impact black-box testing of the application using JMeter.

1. Testing using JMeter is not particularly focused on the internal aspects of an application or program, hence it is often regarded as a black-box testing method. This is because JMeter's main task is to send requests to predefined endpoints, according to the quantity requested by the tester. JMeter acts by evaluating whether these requests can be successfully executed and receiving responses. On the other hand, profiling takes a deeper dive into examining the internal processes of a program when it receives a request. Through profiling, I can identify which parts of the program take the longest time to execute compared to others, allowing for more effective optimization of the code.
2. Through profiling, I can identify which components of the program are slowing down the application's performance in general. This allows me to focus on optimizing those components, which in turn will improve the overall efficiency of the application without having to change many other aspects.
3. Correct, as explained in the tutorial, using the IntelliJ profiler, I can uncover that the most time-consuming part of the program, for instance, the `getAllStudentWithCourse` method, involves excessive looping. This profiler even allows me to see which lines of code within that method most significantly affect its efficiency. With information on how long it takes to execute each function call, it becomes easier for me to identify which components of the program are the main bottlenecks for the overall performance of the application.
4. The biggest challenge I face in performance testing and profiling lies in the ability to interpret relevant output and identify which components of the program act as the main bottlenecks. To overcome this, the solution is to study and understand the output results from JMeter or the profiler more carefully. This may require some time to become familiar with the new technology to better understand the quite detailed information provided.
5. As previously explained, with the profiler from IntelliJ, I can detect which parts of the program are bottleneck, how long it takes to execute a method call, and how often a method is invoked, allowing us to adjust which parts of the program need optimization and which do not. It's important to remember that "premature optimization is the root of all evil" because optimizations that are not needed will only decrease the readability of our code.
6. So far, there haven't been any inconsistencies in the performance testing results produced by the IntelliJ Profiler and JMeter. This indicates that both applications have provided consistent insights into how the application performs in the context of my code testing.
7. Based on strategy number 2, after conducting tests and profiling, the step I take is to evaluate the duration it takes for the program to respond to requests via JMeter. If the response feels slow, I use the profiler to identify which part of the code is causing the delay and then seek solutions to speed up that process. To verify the accuracy of the code post-modification, I ensure that the output remains consistent with before the changes were made. A more effective approach is to create unit tests, as outlined in the previous tutorial. By running unit tests and ensuring they pass, it can be assumed that the refactored code is functioning properly, provided the unit tests are designed correctly and are relevant. This allows focusing on improving only the aspects that truly require enhancement, without needing to modify the entire codebase.