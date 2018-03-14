Over the last months I’ve seen lots of customers trying to tune the thread concurrency inside MySQL with the variable thread_concurrency.
Our advice is: stop wasting your time, it does nothing on GNU/Linux
This variable is specific to Solaris 8 and earlier systems,

https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_thread_concurrency
