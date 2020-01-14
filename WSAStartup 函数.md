# WSAStartup 函数

`WSAStartup`函数通过一个进程来开始使用Winsock DLL

## 语法

```c++
int WSAAPI WSAStartup(
	WORD		wVersionRequested,
    LPWSADATA	lpWSAData
);
```

## 参数

`wVersionRequested`

`lpWSAData`

一个指向`WSAData`结构体的指针，用于接收Windows Sockets实现的细节。

## 返回值

如果成功，`WSAStartup`函数返回零。否则，它返回下面列出的错误码之一。

`WSAStartup`函数会立即在返回值中返回一个扩展的错误码。不必也不应该调用`WSAGetLastError`函数。

| 错误码             | 含义                                                         |
| ------------------ | ------------------------------------------------------------ |
| WSASYSNOTREADY     | 下层的网络子系统未准备好网络通信                             |
| WSAVERNOTSUPPORTED | 特定的Windows Sockets 实现并未提供Windows Sockets支持所需的版本 |
| WSAEINPROGRESS     | 一个阻塞Windows Sockets 1.1的操作正在执行                    |
| WSAEPROCLIM        | WIndows Sockets 实现已经达到了任务支持数量的限制             |
| WSAEFAULT          | `lpWSAData`参数不是合法指针                                  |

## 备注

`WSAStartup`函数必须是一个应用或DLL第一个调用的Windows Sockets函数。它允许一个应用或DLL指定所需的Windows　Sockets版本并收到指定的Windows　Sockets实现的细节。在成功调用`WSAStartup`之后应用程序或DLL才能发出（？）之后的Windows Sockets 函数。



为了支持各种WIndows Sockets 的实现和应用，这些实现和应用可能与最新版本的Windows Sockets规范具有功能性的差异，因此在`WSAStartup`进行了协商。

