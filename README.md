## Spring Boot Scheduling

### Scheduling:
Scheduler is to schedule a thread or task to execute at a certain period of time or periodically at a fixed interval . There are multiple ways of scheduling a task in Java . Java library java.util.TimerTask

### TaskScheduler implementations:
As with Spring's TaskExecutor abstraction, the primary benefit of the TaskScheduler is that code relying on scheduling behavior need not be coupled to a particular scheduler implementation. The flexibility this provides is particularly relevant when running within Application Server environments where threads should not be created directly by the application itself. For such cases, Spring provides a TimerManagerTaskScheduler that delegates to a CommonJ TimerManager instance, typically configured with a JNDI-lookup.

### Enable scheduling annotations:
The @EnableScheduling annotation is used to enable the scheduler for your application. This annotation should be added into the main Spring Boot application class file.
The @Scheduled annotation is used to trigger the scheduler for a specific time period
By default, Spring will use the server's local time zone for the cron expression. However, we can use the zone attribute to change this timezone:
The simple rules that need to be followed to annotate a method with @Scheduled are:
- a method should have the void return type
- a method should not accept any parameters

### Cron:
- * (all) – it is used to specify that event should happen for every time unit. For example, “*” in the <minute> field – means “for every minute”
- ? (any) – it is utilized in the <day-of-month> and <day-of -week> fields to denote the arbitrary value – neglect the field value. For example, if we want to fire a script at “5th of every month” irrespective of what the day of the week falls on that date, then we specify a “?” in the <day-of-week> field
- – (range) – it is used to determine the value range. For example, “10-11” in <hour> field means “10th and 11th hours”
- , (values) – it is used to specify multiple values. For example, “MON, WED, FRI” in <day-of-week> field means on the days “Monday, Wednesday, and Friday”
- / (increments) – it is used to specify the incremental values. For example, a “5/15” in the <minute> field, means at “5, 20, 35 and 50 minutes of an hour”
- L (last) – it has different meanings when used in various fields. For example, if it's applied in the <day-of-month> field, then it means last day of the month, i.e. “31st for January” and so on as per the calendar month. It can be used with an offset value, like “L-3“, which denotes the “third to last day of the calendar month”. In the <day-of-week>, it specifies the “last day of a week”. It can also be used with another value in <day-of-week>, like “6L“, which denotes the “last Friday”
- W (weekday) – it is used to specify the weekday (Monday to Friday) nearest to a given day of the month. For example, if we specify “10W” in the <day-of-month> field, then it means the “weekday near to 10th of that month”. So if “10th” is a Saturday, then the job will be triggered on “9th”, and if “10th” is a Sunday, then it will trigger on “11th”. If you specify “1W” in the <day-of-month> and if “1st” is Saturday, then the job will be triggered on “3rd” which is Monday, and it will not jump back to the previous month
- \# it is used to specify the “N-th” occurrence of a weekday of the month, for example, “3rd Friday of the month” can be indicated as “6#3“

### Fixed Rate:
Fixed Rate scheduler is used to execute the tasks at the specific time. It does not wait for the completion of previous task. The values should be in milliseconds

### Fixed Delay:
Fixed Delay scheduler is used to execute the tasks at a specific time. It should wait for the previous task completion. The values should be in milliseconds.




further references:     
- https://spring.io/guides/gs/scheduling-tasks/
- https://www.baeldung.com/cron-expressions
- https://www.tutorialspoint.com/spring_boot/spring_boot_scheduling.htm#:~:text=Scheduling%20is%20a%20process%20of,scheduler%20on%20the%20Spring%20applications.



### Project Descriptions:
please see application.properties files in resources folder and select a active profile "dev" or "com" to run project. you can check test methods too.  
run project and check console. 

### IntellliJ IDEA Configurations:
- IntelijIDEA: Help -> Edit Custom Vm Options -> add these two line:
    - -Dfile.encoding=UTF-8
    - -Dconsole.encoding=UTF-8
- IntelijIDEA: File -> Settings -> Editor -> File Encodings-> Project Encoding: form "System default" to UTF-8. May be it affected somehow.
- IntelijIDEA: File -> Settings -> Editor -> General -> Code Completion -> check "show the documentation popup in 500 ms"
- IntelijIDEA: File -> Settings -> Editor -> General -> Auto Import -> check "Optimize imports on the fly (for current project)"
- IntelijIDEA: File -> Settings -> Editor -> Color Scheme -> Color Scheme Font -> Scheme: Default -> uncheck "Show only monospaced fonts" and set font to "Tahoma"
- IntelijIDEA: Run -> Edit Configuration -> Spring Boot -> XXXApplication -> Environment -> VM Options: -Dspring.profiles.active=dev

<hr/>
<a href="mailto:eng.motahari@gmail.com?"><img src="https://img.shields.io/badge/gmail-%23DD0031.svg?&style=for-the-badge&logo=gmail&logoColor=white"/></a>


