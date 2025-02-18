***first.sh***
```bash
#!/bin/sh
# This is a comment!
echo Hello World        # This is a comment, too!
```
**The first line tells Unix that the file is to be executed by /bin/sh.** This is the standard location of the Bourne shell on just about every Unix system. If you're using GNU/Linux, /bin/sh is normally a symbolic link to bash (or, more recently, dash).

***export*** 命令是用来将 shell 环境变量导出到子进程中的。在 shell 中定义的变量，默认只对当前 shell 会话有效。如果你希望这个变量在当前 shell 会话及其启动的所有子进程（如脚本或其他程序）中都有效，就需要使用 export。
基本用法：
export VAR_NAME=value
这会创建一个名为 VAR_NAME 的环境变量，并将它的值设置为 value，同时确保这个变量可以被当前 shell 启动的任何子进程（包括脚本）访问到。

***${VAR}*** 是一种更通用的引用变量的方式，尤其在涉及到变量拼接或复杂情况时，它可以避免歧义。虽然在简单情况下，$VAR 和 ${VAR} 的效果是一样的，但 ${VAR} 在处理一些复杂表达式时更加安全和清晰。

在 shell 中，如果你引用了一个不存在的变量（即未定义的变量），通常它的值会被视为空字符串，且不会报错或显示任何信息。这是 shell 中的一种标准行为，目的是保持脚本的健壮性。

**使用 source 或 . 执行脚本时**，脚本和当前 shell 在同一个进程中运行，脚本修改的变量会影响当前 shell。
如果你使用普通的 ./myvar.sh 执行脚本，那么脚本将在子进程中执行，子进程的环境变量不会影响到当前 shell，除非你使用 export 来显式地传递环境变量。

However,**"**, **$**, **`**, and \ are still interpreted by the shell, even when they're in double quot
**The backslash (\\) character is used to mark these special characters so that they are not interpreted by the shell**, but passed on to the command being run (for example, echo).
### FOR LOOP
```bash
#!/bin/sh
for i in hello 1 * 2 goodbye 
do
  echo "Looping ... i is set to $i"
done


Looping ... i is set to hello
Looping ... i is set to 1
Looping ... i is set to (name of first file in current directory)
    ... etc ...
Looping ... i is set to (name of last file in current directory)
Looping ... i is set to 2
Looping ... i is set to goodbye
```

### WHILE LOOP<br> 
The colon (:) always evaluates to true<br>
```bash
mkdir rc{0,1,2,3,4,5,6,S}.d<br>
```
### TEST [
This means that '[' is actually a program, just like ls and other programs, so it must be surrounded by spaces.<br>
Note: Some shells also accept "==" for string comparison; this is not portable, a single "=" should be used for strings, or "-eq" for integers.<br>
I've highlighted the mandatory spaces with the word ***'SPACE'*** - replace 'SPACE' with an actual space; if there isn't a space there, it won't work:
```bash
if SPACE [ SPACE "$foo" SPACE = SPACE "bar" SPACE ]
```
Test is most often invoked indirectly via the if and while statements.
```bash
if [ ... ]
then
  # if-code
else
  # else-code
fi
```
```bash
if  [ something ]; then
 echo "Something"
 elif [ something_else ]; then
   echo "Something else"
 else
   echo "None of the above"
fi
```
```bash
#!/bin/sh
if [ "$X" -lt "0" ]
then
  echo "X is less than zero"
fi
if [ "$X" -gt "0" ]; then
  echo "X is more than zero"
fi
[ "$X" -le "0" ] && \
      echo "X is less than or equal to  zero"
[ "$X" -ge "0" ] && \
      echo "X is more than or equal to zero"
[ "$X" = "0" ] && \
      echo "X is the string or number \"0\""
[ "$X" = "hello" ] && \
      echo "X matches the string \"hello\""
[ "$X" != "hello" ] && \
      echo "X is not the string \"hello\""
[ -n "$X" ] && \
      echo "X is of nonzero length"
[ -f "$X" ] && \
      echo "X is the path of a real file" || \
      echo "No such file: $X"
[ -x "$X" ] && \
      echo "X is the path of an executable file"
[ "$X" -nt "/etc/passwd" ] && \
      echo "X is a file which is newer than /etc/passwd"
```
Note that we can use the semicolon (;) to join two lines together. This is often done to save a bit of space in simple if statements.<br>
The backslash (\) serves a similar, but opposite purpose: it tells the shell that this is not the end of the line, but that the following line should be treated as part of the current line. This is useful for readability. It is customary to indent the following line after a backslash (\) or semicolon (;).<br><br>
There is a simpler way of writing if statements: The && and || commands give code to run if the result is true, or false, respectively.
