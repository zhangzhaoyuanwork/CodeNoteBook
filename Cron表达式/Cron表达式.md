## **Cron表达式**

### **基本结构**

*   **组成**：
    *   Cron表达式通常包含六个或七个域，每个域代表不同的时间单位。
    *   当不包括“年”域时，其格式为：`[秒] [分] [时] [日] [月] [周]`。
    *   若包含“年”域，则完整格式为：`[秒] [分] [时] [日] [月] [周] [年]`。
    *   各域之间用空格分隔。
    *   Cron表达式周域与日域是or的关系，只需满足其一即执行，其他域为and关系必须全部满足才可执行。

### **各域含义及允许值**

*   **秒**：取值范围通常是0\~59的整数，支持特殊字符 `*`, `,`, `-`, `/`。

*   **分**：取值范围同样是0\~59的整数，支持特殊字符 `*`, `,`, `-`, `/`。

*   **时**：取值范围是0\~23（24小时制），支持特殊字符 `*`, `,`, `-`, `/`。

*   **日**：取值范围通常为1\~31（取决于月份），支持特殊字符 `*`, `,`, `-`, `/`, `?`, `L`, `W`, `LW`。

*   **月**：可以用数字（1\~12）表示，也可用英文缩写（如 `JAN`、`FEB` 等）或全称。支持特殊字符 `*`, `,`, `-`, `/`。

*   **周**：取值范围是0-7/1-7对应周日至周六(0和7/1为周日)，也可用英文缩写（`MON TUE WED THU FRI SAT SUN`）或全称。特殊字符如 `L` 可用于指定最后一天，`#` 可用于指定第几周的某天。Linux和Spring的允许值为0-7，0和7为周日，Quartz的允许值为1-7，1为周日。支持特殊字符 `*`, `,`, `-`, `/`, `?`, `L`, `#`。

*   **年**（可选）：四位数表示年份，如 `2024`。可以使用通配符 `?` 或者指定范围（如 `2018-2025`）来匹配年份。支持特殊字符 `*`, `,`, `-`, `/`。

### **特殊字符与通配符**

*   **星号 (`*`)**：代表任意值。例如，在“分钟”域使用 `*` 表示每分钟都触发。

*   **问号 (`?`)**：代表不在乎的值，只能用在日和星期两个域，因为两者可能彼此矛盾，相互影响。

*   **逗号 (`,`)**：用于列举多个独立值。例如，`1,15,30` 表示在第1、15、30分钟触发。

*   **减号 (`-`)**：定义一个范围。如 `10-15` 表示从第10分钟到第15分钟内每分钟触发。

*   **斜线 (`/`)**：用于定义步进值。如 `*/5` 表示每隔5个单位（如每隔5分钟）触发一次。

*   **字母 L**：在“日”域表示一个月的最后一天，在“周”域表示一个月的最后一个星期几。

*   **字母 W**：只能用在“日”域，指定离给定日期最近的工作日（周一到周五）。

*   **字母 LW**：只能用在“日”域，指定这个月最后一个工作日。

*   **井号 (#)**：在“周”域与 `L` 结合使用，表示一个月内第几个星期几，如 `5#3` 表示第三周的星期五。

### **Cron表达式示例**

```cron
#每小时的第30分钟执行
0 30 * * * ? 

#每周一至周五的上午9点至下午5点，每1分钟执行一次
0 */1 9-17 ? * 1-5

#每月的第一天和最后一天的凌晨1点执行
0 0 1 1,L * ?

#每年的10月24日凌晨0点0分执行一次
0 0 0 24 10 ?

#每月的第三个星期五上午10:15触发
0 15 10 ? * 5#3

#每月的4号与周一到周三的11点
0 0 11 4 * 1-3
```

### crontab使用

*   查看当前用户的定时任务

```shell
crontab -l #查看当前用户的定时任务
```

*   编辑当前用户的定时任务

```shell
crontab -e #编辑当前用户的定时任务
```

*   删除当前用户的定时任务

```shell
crontab -r #删除当前用户的定时任务
```

### **Cron表达式应用**

Cron表达式广泛应用于各种定时任务调度系统中，如：

*   **Quartz**：一个流行的Java作业调度框架，使用Cron表达式来定义作业的触发时间。星期域取值1-7，1为周日。

*   **Spring框架的`@Scheduled`注解**：在Spring应用程序中，可以使用Cron表达式来配置方法的定时执行。星期域取值0-7,0和7为周日。

*   **Linux系统的cron服务**：通过crontab命令编辑cron条目，使用Cron表达式控制定时任务在服务器上的执行。星期域取值0-7,0和7为周日。

