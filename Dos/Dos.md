## Dos常用命令

### **目录操作类命令**

*   **`MD` / `MKDIR`**:
    *   作用：创建一个新的子目录。
    *   语法：`md [C:][path]<subPath>` 或 `mkdir [C:][path]<subPath>`
    *   示例：`md Documents\NewFolder` 创建名为“NewFolder”的子目录在当前用户的“Documents”目录下。

*   **`CD`**:
    *   作用：更改当前工作目录或显示当前目录路径。
    *   语法：`cd [C:][path]`
    *   示例：`cd ..` 进入上级目录；`cd C:\Windows\System32` 进入指定目录。

*   **`RD` / `RMDIR`**:
    *   作用：删除一个空目录。
    *   语法：`rd [C:][path]<subPath>` 或 `rmdir [C:][path]<subPath>`
    *   示例：`rd OldFolder` 删除当前目录下名为“OldFolder”的空目录。

*   **`DIR`**:
    *   作用：列出当前目录或指定目录中的文件和子目录信息。
    *   语法：`dir [C:][path][options]`
    *   示例：`dir /A` 显示所有文件（包括隐藏文件）；`dir /S` 递归显示子目录中的文件。

*   **`TREE`**:
    *   作用：以树状结构显示目录及其子目录。
    *   语法：`tree [drive:][path] [/F] [/A]`
    *   示例：`tree /F` 显示当前目录及其子目录的详细树形结构。

*   **`盘符:`**:
    *   作用：（非标准命令）进入不同磁盘或分区。
    *   语法：`[盘符:]`
    *   示例：`c:` 进入c盘

### **文件操作类命令**

*   **`COPY`**:
    *   作用：复制文件或目录。
    *   语法：`copy source destination`
    *   示例：`copy file.txt backup.txt` 复制“file.txt”至“backup.txt”；`copy C:\SourceDir D:\BackupDir` 复制整个目录及其内容。

*   **`DEL` / `ERASE`**:
    *   作用：删除一个或多个文件。
    *   语法：`del [C:][path]<filename>[...][options]` 或 `erase [C:][path]<filename>[...][options]`
    *   示例：`del *.tmp` 删除当前目录下所有扩展名为“tmp”的文件；`del /Q file.txt` 强制删除无需确认。

*   **`MOVE`**:
    *   作用：移动文件或重命名文件（也可以移动目录，但不能跨卷移动）。
    *   语法：`move source destination`
    *   示例：`move file.txt NewFile.txt` 重命名文件；`move C:\TempFiles\*.* C:\Archives` 移动所有文件至“Archives”目录。

*   **`REN` / `RENAME`**:
    *   作用：重命名一个文件或目录。
    *   语法：`ren [C:][path]<oldName> <newName>` 或 `rename [C:][path]<oldName> <newName>`
    *   示例：`ren OldFileName.txt NewFileName.txt` 改变文件名。

*   **`TYPE`**:
    *   作用：显示文本文件的内容。
    *   语法：`type [C:][path]<filename>`
    *   示例：`type README.txt` 打印“README.txt”文件内容到屏幕。

### **时间与日期类命令**

*   **`DATE`**:
    *   作用：显示或设置当前系统的日期。
    *   语法：`date [/T]`（显示当前日期）或 `date mm-dd-yyyy`（设置日期）
    *   示例：`date 0¾-21-2023` 设置系统日期为2023年3月21日。

*   **`TIME`**:
    *   作用：显示或设置当前系统的时钟时间。
    *   语法：`time [/T]`（显示当前时间）或 `time hh:mm:ss[.xxx]`（设置时间）
    *   示例：`time 15:30:45` 设置系统时间为下午3点30分45秒。

*   **`TIMESTAMP`**:
    *   作用（非标准命令，需在批处理文件中实现）：在命令行输出中添加当前日期和时间戳。
    *   示例（在批处理文件中）：
        ```batch
        @echo off
        echo %date% %time%
        rem ... 其他命令 ...
        ```


### **其他常用命令**

*   **`CLS`**:
    *   作用：清除命令提示符窗口中的显示内容。
    *   语法：`cls`
    *   示例：直接输入 `cls` 即可清空当前屏幕。

*   **`EXIT`**:
    *   作用：退出DOS命令行界面。
    *   语法：`exit`
    *   示例：直接输入 `exit` 结束当前命令提示符会话。

*   **`ATTRIB`**:
    *   作用：修改或查看文件或目录的属性（如只读、隐藏、系统等）。
    *   语法：`attrib [+/−][RSHAC] [filespec][...][/S [/D]]`
    *   示例：`attrib +H secret.txt` 将“secret.txt”设置为隐藏。


*   **`HELP` / `/?`**:
    *   作用：获取某个命令的帮助信息或显示所有可用命令列表。
    *   语法：`help <command>` 或 `<command> /?`
    *   示例：`help dir` 或 `dir /?` 查看`dir`命令的详细帮助。

*   **`PATH`**:
    *   作用：设置或显示当前命令搜索路径。
    *   语法：`path [pathlist]`（设置）或 `path`（显示）
    *   示例：`path %PATH%;C:\CustomTools` 添加“C:\CustomTools”到系统路径中。

*   **`CHDIR` / `CHDRIVE`**:
    *   作用：分别用于改变当前目录或切换当前驱动器。
    *   语法：`chdir [C:][path]` 或 `chdrive [drive:]`
    *   示例：`chdir C:\Program Files` 切换到指定目录；`chdrive D:` 切换到D盘。



### **网络类命令**

*   **`ipconfig`**:
    *   作用：显示或配置网络接口卡（NIC）的IP地址、子网掩码、默认网关等TCP/IP配置信息。
    *   语法：`ipconfig [options]`
    *   示例与选项说明：
        *   `ipconfig`: 显示所有活动网络接口的基本信息。
        *   `ipconfig /all`: 显示所有网络接口的详细信息，包括物理地址（MAC地址）、DNS服务器、DHCP租约状态等。
        *   `ipconfig /release [adapter]`: 释放指定网络接口的IP地址（默认为所有接口），通常用于与DHCP服务器断开连接。
        *   `ipconfig /renew [adapter]`: 重新从DHCP服务器获取IP地址（默认为所有接口）。
        *   `ipconfig /flushdns`: 清除本地DNS解析缓存。
        *   `ipconfig /displaydns`: 显示当前DNS解析缓存的内容。
        *   `ipconfig /registerdns`: 强制重新注册DNS和NetBIOS名称。

*   **`PING`**:
    *   作用：测试网络连通性，通过发送ICMP Echo Request消息并接收响应来判断目标主机是否可达。
    *   语法：`ping [options] <target>`
    *   示例：`ping www.google.com` 测试与Google网站的连通性；`ping -n 5 192.168.1.1` 向指定IP发送5个数据包。

*   **`TELNET`**:
    *   作用：通过TCP连接远程登录到设备（如服务器、网络设备等）并交互式操作。
    *   语法：`telnet <hostname> [<port>]`
    *   示例：`telnet mail.server.com 25` 登录到mail.server.com的SMTP服务端口进行调试。


### **输出及重定向类命令**

*   **`ECHO`**:
    *   作用：在命令行输出指定的文本或字符串，常用于创建批处理文件中的注释或打印变量值。
    *   语法：`echo [on|off]`（开关命令回显）或 `echo <message>`（打印消息）
    *   示例：`echo Hello, World!` 输出“Hello, World!”；`echo %USERNAME%` 输出当前用户名。

*   **`>`**:
    *   作用：重定向命令的标准输出（STDOUT），即将命令执行结果写入到指定文件，如果目标文件已存在，则覆盖原有内容。
    *   语法：`command > file`
    *   示例：`dir > directory_listing.txt` 将`dir`命令的输出保存到“directory\_listing.txt”文件中。

*   **`>>`**:
    *   作用：追加重定向命令的标准输出，即将命令执行结果附加到指定文件末尾，不会覆盖原有内容。
    *   语法：`command >> file`
    *   示例：`ipconfig >> network_info.txt` 将`ipconfig`命令的输出追加到“network\_info.txt”文件中。

* **管道（`|`）**

    *   **作用**：将前一个命令的标准输出作为后一个命令的标准输入，实现命令链式处理。
    *   **语法**：`command1 | command2`
    *   **示例**：`dir /b | findstr ".txt"` 列出当前目录下所有文件（不带详细信息），并将结果传递给`findstr`命令查找以“.txt”结尾的文件名。

### **注释**

在DOS/命令提示符环境中，批处理文件（`.bat`）中使用注释的方法如下：

*   **`REM` 或 `::`**:
    *   作用：在批处理文件中添加注释，注释内容将被命令解释器忽略，不会被执行。
    *   语法：
        ```batch
        REM 注释内容
        :: 注释内容
        ```
    *   示例：
        ```batch
        REM This is a comment explaining the following command
        dir /B

        :: Display system date and time
        echo %date% %time%
        ```


