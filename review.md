***export*** 命令是用来将 shell 环境变量导出到子进程中的。在 shell 中定义的变量，默认只对当前 shell 会话有效。如果你希望这个变量在当前 shell 会话及其启动的所有子进程（如脚本或其他程序）中都有效，就需要使用 export。
基本用法：
export VAR_NAME=value
这会创建一个名为 VAR_NAME 的环境变量，并将它的值设置为 value，同时确保这个变量可以被当前 shell 启动的任何子进程（包括脚本）访问到。

***${VAR}*** 是一种更通用的引用变量的方式，尤其在涉及到变量拼接或复杂情况时，它可以避免歧义。虽然在简单情况下，$VAR 和 ${VAR} 的效果是一样的，但 ${VAR} 在处理一些复杂表达式时更加安全和清晰。

在 shell 中，如果你引用了一个不存在的变量（即未定义的变量），通常它的值会被视为空字符串，且不会报错或显示任何信息。这是 shell 中的一种标准行为，目的是保持脚本的健壮性。

使用 source 或 . 执行脚本时，脚本和当前 shell 在同一个进程中运行，脚本修改的变量会影响当前 shell。
如果你使用普通的 ./myvar.sh 执行脚本，那么脚本将在子进程中执行，子进程的环境变量不会影响到当前 shell，除非你使用 export 来显式地传递环境变量。

However, ", $, `, and \ are still interpreted by the shell, even when they're in double quotes.
The backslash (\) character is used to mark these special characters so that they are not interpreted by the shell, but passed on to the command being run (for example, echo).
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
mkdir rc{0,1,2,3,4,5,6,S}.d<br>
