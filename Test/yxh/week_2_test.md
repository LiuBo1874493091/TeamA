1-1.

2-1.:a:输出六次hello world。
	 第一次循环，fork()产生第一个子进程，父子进程都打印hello world。
		子进程获得父进程的数据空间和堆栈的副本，即子进程剩余一次循环。
		子进程进行第二次循环，产生子子进程，子进程和子子进程打印hello world。
		子子进程获得子进程数据副本，不再循环，子进程也停止。
	 第二次循环，又产生一个子进程。
		同上，该子进程打印hello world后结束，父进程打印后也结束，共打印六次。
	 b:最终产生了两个子进程和一个子子进程。 
	

2-2.exec系列函数就是用（通过文件描述符或者路径名或者文件名）指定的程序替换掉原进程执行的程序
	exec系列函数不产生新的进程，是对原有的进程进行操作

2-3.cat先获取父进程的所有输出，再获取子进程的所有输出。
	子进程复制了父进程的所有文件描述符和堆栈数据，其中包括标准输出，所以虽然第一个打印语句子进程不执行，却能打印出来。