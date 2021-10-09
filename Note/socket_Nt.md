socket_Nt



https://www.cnblogs.com/straight/articles/7660889.html#:~:text=bind%20%28%29%E5%87%BD%E6%95%B0%E6%8A%8A%E4%B8%80%E4%B8%AA%E5%9C%B0%E5%9D%80%E6%97%8F%E4%B8%AD%E7%9A%84%E7%89%B9%E5%AE%9A%E5%9C%B0%E5%9D%80%E8%B5%8B%E7%BB%99socket%E3%80%82%20%E4%BE%8B%E5%A6%82%E5%AF%B9%E5%BA%94AF_INET%E3%80%81AF_INET6%E5%B0%B1%E6%98%AF%E6%8A%8A%E4%B8%80%E4%B8%AAipv4%E6%88%96ipv6%E5%9C%B0%E5%9D%80%E5%92%8C%E7%AB%AF%E5%8F%A3%E5%8F%B7%E7%BB%84%E5%90%88%E8%B5%8B%E7%BB%99socket%E3%80%82%20%E2%80%A2%20sockfd%20%EF%BC%9A%E5%8D%B3socket%E6%8F%8F%E8%BF%B0%E5%AD%97%EF%BC%8C%E5%AE%83%E6%98%AF%E9%80%9A%E8%BF%87socket%20%28%29%E5%87%BD%E6%95%B0%E5%88%9B%E5%BB%BA%E4%BA%86%EF%BC%8C%E5%94%AF%E4%B8%80%E6%A0%87%E8%AF%86%E4%B8%80%E4%B8%AAsocket%E3%80%82,bind%20%28%29%E5%87%BD%E6%95%B0%E5%B0%B1%E6%98%AF%E5%B0%86%E7%BB%99%E8%BF%99%E4%B8%AA%E6%8F%8F%E8%BF%B0%E5%AD%97%E7%BB%91%E5%AE%9A%E4%B8%80%E4%B8%AA%E5%90%8D%E5%AD%97%E3%80%82%20%E2%80%A2%20addr%20%EF%BC%9A%E4%B8%80%E4%B8%AAconst%20struct%20sockaddr%20%2A%E6%8C%87%E9%92%88%EF%BC%8C%E6%8C%87%E5%90%91%E8%A6%81%E7%BB%91%E5%AE%9A%E7%BB%99sockfd%E7%9A%84%E5%8D%8F%E8%AE%AE%E5%9C%B0%E5%9D%80%E3%80%82

一篇很棒的博客

**常用头文件**

```
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
#include<stdio.h>
#include <stdlib.h> 
#include <string.h>
#include <ctype.h>
#include <errno.h>
#include <malloc.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <sys/ioctl.h>
#include <stdarg.h>
#include <fcntl.h>
```



**网络通信socket**

```
socket就是插座（中文翻译成套接字有点莫名其妙），运行在计算机中的两个程序通过socket建立起一个通道，数据在通道中传输。
socket把复杂的TCP/IP协议族隐藏了起来，对程序员来说，只要用好socket相关的函数，就可以完成网络通信。
```



**socket的分类**

```
socket提供了流（stream）和数据报（datagram）两种通信机制，即流socket和数据报socket。
流socket基于TCP协议，是一个有序、可靠、双向字节流的通道，传输数据不会丢失、不会重复、顺序也不会错乱。就像两个人在打电话，接通后就在线了，您一句我一句的聊天。

数据报socket基于UDP协议，不需要建立和维持连接，可能会丢失或错乱。UDP不是一个可靠的协议，对数据的长度有限制，但是它的速度比较高。就像短信功能，一个人向另一个人发短信，对方不一定能收到。
```



**客户/服务端模式**

```
在TCP/IP网络应用中，两个程序之间通信模式是客户/服务端模式（client/server），客户/服务端也叫作客户/服务器，各人习惯。

客户/服务端工作流程如下图：
```

![socket的C-S模型](D:\work\Myhub\Note\Picture\socket的C-S模型.png)



**库函数**

```
1.socket	创建一个新的socket，
	int socket(int domain, int type, int protocol);
	
	domain：协议域，又称协议族（family）。常用的协议族有AF_INET、AF_INET6、AF_LOCAL（或称AF_UNIX，	Unix域Socket）、AF_ROUTE等。协议族决定了socket的地址类型，在通信中必须采用对应的地址，如AF_INET决	定了要用ipv4地址（32位的）与端口号（16位的）的组合、AF_UNIX决定了要用一个绝对路径名作为地址。

	type：指定socket类型。常用的socket类型有SOCK_STREAM、SOCK_DGRAM、SOCK_RAW、SOCK_PACKET、	SOCK_SEQPACKET等。流式socket（SOCK_STREAM）是一种面向连接的socket，针对于面向连接的TCP服务应用。	数据报式socket（SOCK_DGRAM）是一种无连接的socket，对应于无连接的UDP服务应用。
 
	protocol：指定协议。常用协议有IPPROTO_TCP、IPPROTO_UDP、IPPROTO_STCP、IPPROTO_TIPC等，分别对	应TCP传输协议、UDP传输协议、STCP传输协议、TIPC传输协议。

	说了一大堆废话，第一个参数只能填AF_INET，第二个参数只能填SOCK_STREAM，第三个参数只能填0。
	除非系统资料耗尽，socket函数一般不会返回失败。

	返回值：成功则返回一个socket，失败返回-1，错误原因存于errno 中。
	
2.gethostbyname
	struct hostent *gethostbyname(const char *name);
	
	参数name，域名或者主机名，例如"192.168.1.3"、"www.freecplus.net"等。

	返回值：如果成功，返回一个hostent结构指针，失败返回NULL。

	gethostbyname只用于客户端。

	gethostbyname只是把字符串的ip地址转换为结构体的ip地址，只要地址格式没错，一般不会返回错误。失败时不会		设置errno的值。

3.bind
	int bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
	bind()函数把一个地址族中特定的地址赋给socket，例如对应AF_INET、AF_INET6就是把一个ipv4或ipv6地址和	  端口号组合赋给socket。
	
	函数的三个参数分别为： 
        •sockfd：即socket描述字，它是通过socket()函数创建了，唯一标识一个socket。bind()函数就是将给这		   个描述字绑定一个名字。 
		
		•addr：一个const struct sockaddr *指针，指向要绑定给sockfd的协议地址。
	
		•addrlen：对应的是地址的长度。 
			通常服务器在启动的时候都会绑定一个众所周知的地址（如ip地址+端口号），用于提供服务，客户就可以通			 过它来接连服务器；而客户端就不用指定，有系统自动分配一个端口号和自身的ip地址组合。这就是为什么			 通常服务器端在listen之前会调用bind()，而客户端就不会调用，而是在connect()时由系统随机生成一			 个。

4.listen()、connect()函数
	int listen(int sockfd, int backlog);
		blacklog:服务器处理一个连接需要时间，在这段时间里面除了第一个连接请求是正在进行处理以外，其他的连接		  请求都在请求队列中等待，而如果超过了队列的最大等待个数时，其他的请求将被忽略或者将不会被处理。
		
	int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
	
	如果作为一个服务器，在调用socket()、bind()之后就会调用listen()来监听这个socket，如果客户端这时调用		connect()发出连接请求，服务器端就会接收到这个请求。
	
5.accept()函数
	int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
		sockfd:服务端的socket描述字
		
		addr:返回客户端的协议地址
		
		addrlen:客户端协议地址的长度
		
		accept()的返回值是一个由内核自动生成的描述字，表示和客户端之间的TCP连接，内核为每个由服务器进程接		  受的客户连接创建了一个已连接socket描述字，当服务器完成了对某个客户的服务，相应的已连接socket描述字		 就被关闭。
		
	TCP服务器端依次调用socket()、bind()、listen()之后，就会监听指定的socket地址了。TCP客户端依次调用	 socket()、connect()之后就向TCP服务器发送了一个连接请求。TCP服务器监听到这个请求之后，就会调用			accept()函数取接收请求，这样连接就建立好了。之后就可以开始网络I/O操作了，即类同于普通文件的读写I/O。
	
6.网络I/O操作相关函数
    •read()/write() 
    •recv()/send() 
    •readv()/writev() 
    •recvmsg()/sendmsg() 
    •recvfrom()/sendto()
```

**sockaddr结构体**

```
struct sockaddr{
	unsingned short sa_family;	//地址类型
	char sa_data[14];		//14字节的端口和地址
}；
struct sockaddr_in{
	short int sin_family;	//地址类型
	unsigned short int sin_port;	//端口号
	struct in_addr sin_addr;	//地址
	unsigned char sin_zero[8];	//为了保持与sockaddr一样的长度
}
struct in_addr{
	unsigned long s_addr;	//地址
}

struct hostent{
	char* h_name;	//主机名
	char** h_aliases;	//主机所有别名构成的字符串数组，同一ip可以绑定多个域名
	int h_addrtype;	//主机地址类型
	int h_length;	//主机地址长度，ipv4为4，ipv6为16
	char **h_addr_list;		//以网络字节序存储的主机地址
};
#define h_addr h_addr_list[0]

struct timeval {  
int tv_sec;     //seconds  
int tv_usec;    //microseconds，注意这里是微秒不是毫秒  
};


htons将主机的无符号短整形数转换成网络字节顺序 
htonl将主机的无符号长整形数转换成网络字节顺序

in_addr_t inet_addr(const char *cp);
	把字符串转化为网络字节序的地址

char *inet_ntoa(struct in_addr in);
	把网络字节序地址转化为字符串IP地址

int inet_aton(const char *cp, struct in_addr *inp);
	将字符串IP地址转化为32位网络字节序IP地址，地址不正确返回0，没有错误码存入errno中
```
