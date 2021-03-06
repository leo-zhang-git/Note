**第一章 概述**
<br>
    1.1计算机网络在信息时代的作用
        

        21世纪的重要特征是数字化、网络化、信息化，它是一个以网络为核心的信息时代
        三大网络是：电信网络、有线电视网络、计算机网络
        
        互联网的两个重要基本特点：
            联通性：使上网用户间可以交换信息
            共享：指资源共享，资源共享是多方面的，可以是信息、软件共享，也可以是硬件共享。
<br>
    1.2互联网概述
        
        网络的网络：
            计算机网络（简称为网络〉由若干结点（node）和连接这些结点的链路(link）组成 。
            网络之间还可以通过路由器互连起来，这就构成了一个覆盖范围更大的计算机网络。
            这样的网络称为互连网（internetwork/internet），如图 1-l(b）所示。因此互连网是“网络的
            网络”（network of networks）。
            
        internet（互连网）：多个计算机网络互联而成的计算机网络
        Internet（互联网）：特指全球最大的、开放的、由众多网络相互连接而成的特定互连网，它采用TCP/IP协议族作为						通信规则，前身是美国ARPANET阿帕网
        
        互联网基础结构发展的三个阶段：
        	一：从单个网络ARPANET向互连网发展的过程，把1983年作为互联网的诞生时间，因为当年TCP/IP协议成为阿帕			网的标准协议，使得所有使用TCP/IP协议的计算机能够相互通信
        	
        	二：建成三级结构的互联网（主干网、地区网、校园网/企业网）                                                                                                                                     三：逐渐形成了多层次ISP结构的互联网。主干网NSFNET（美国国家科学基金网）逐渐被多个商用的互联网主干网		   替代，出现了互联网服务提供者ISP（Internet Service Provider）
       
       随着互联网上数据流量的急剧增长，互联网交换点IXP（Internet eXchange Point）诞生了，IXP的作用是允许两	    个网络直接相连并交换分组，而不需要通过第三个网络转发分组
![基于ISP的多层结构的互联网](D:\work\Note_git\Note\Picture\基于ISP的多层结构的互联网.png)<br>
    1.3互联网的组成

        从工作方式上看，可以分为两大块：
            边缘部分：
                由所有连接在互联网上的主机组成。这部分是用户直接使用的，用来进
                行通信（传送数据、音频或视频）和资源共享。
            核心部分：
                由大量网络和连接这些网络的路由器组成。这部分是为边缘部分提供服
                务的 （提供连通性和交换。
        
        1.3.1互联网的边缘部分：
    
            “计算机之间通信”是指“主机 的某个进程和主机 上的另一个进程进行通信”
            在网络边缘的端系统之间的通信方式通常可划分为两大类 ：
                客户一服务器方式（C/S方式）
                对等方式 （P2P 方式〉
    
        1.3.2互联网的核心部分：
    
            在网络核心部分起特殊作用的是路由器（router），它是一种专用计算机 但不叫做主
            机〉。路由器是实现分组交换(packet switching）的关键构件，其任务是转发收到的分组，这是
            网络核心部分最重要的功能。
            为了弄清分组交换 下面先介绍电路交换的基本概念。
    
            1.电路交换：
    
                从通信资源的分配角度来看， 交换 (switching)就是按照某种方式动态地分配传输线路的资源
                经过“建立连接 （占用通信资源〉→通话 （一直占用通信资源〉呻释放连接 （归还通信资
                源）”三个步骤的交换方式称为电路交换。
                电路交换的一个重要特点就是在通话的全部时间内 通话的两个用户始终占用端到端的通信资源
            
            2.分组交换： 特点：存储转发
    
    			优点：高效、灵活、迅速、可靠
                分组交换则采用存储转发技术
                我们把要发送的整块数据称为一个报文 (message)
                先把较长的报文划分成为一个个更小的等长数据段，在每一个数据段前面，加上一些由必要的控
                制信息组成的首部(header）后，就构成了一个分组(packet）。分组又称为“ ”，而分组的首部
                也可称为“包头”
                主机是为用户进行信息处理的， 并且可以和其他主机通过网络交换信息。 路由器则
                是用来转发分组的，即进行分组交换的。
    
                电路交换
                    整个报文的比特流连续地从源点直达终点，好像在一个管道中传送。
                
                报文交换
                    整个报文先传送到相邻结点，全部存储下来后查找转发表，转发到下一个结点。
                
                分组交换
                    单个分组（这只是整个报文的一部分）传送到相邻结点，存储下来后查找转发表，
                    转发到下一个结点   
<br>

1.5计算机网络的类别
        

    计算机网络的精确定义并未统一。
    
    关于计算机网络的较好的定义是这样的：
        计算机网络主要是由一些通用的、可编程的硬件互连而成的，而这些硬件并非专门用来实现某特定目的 
        例如，传送数据或视频信号）。这些可编程的硬件能够用来传送多种不同类型的数据，并能支持广泛的
        和日益增长的应用。
    
    根据这个定义：
        计算机网络所连接的硬件，并不限于一般的计算机，而是包括了智能手机
        计算机网络并非专门用来传送数据，而是能够支持很多种的应用 （包括今后可能出现的各种应用〉
    
    1. 按照网络的作用范围进行分类：
    
        广域网 WAN (wide Area Network)
    
        城域网 MAN (Metropolitan Area Network)
    
        局域网 LAN (Local Area Network)
        
        个人区域网 PAN(personal Area Network)
        
        顺便指出，若中央处理机之间的距离非常近（如仅 米的数量级或甚至更小些），则一
        般就称之为多处理机系统而不称它为计算机网络
        
    2.按照网络的使用者进行分类
        
        公用网(public network) 
            这是指电信公司（国有或私有〉出资建造的大型网络“公用”的意思就是所有愿意按电信公司的规定
            交纳费用的人都可以使用这种网络。因此公用网也可称为公众网
    
        专用网(private network) 
            这是某个部门为满足本单位的特殊业务工作的需要而建造的网络。这种网络不向本单位以外的人提
            供服务 例如，军队、铁路、银行、电力等系统均有本系统的专用网。
        
    3.用来把用户接入到互联网的网络
    
        这种网络就是接入网 AN (Access Network），它又称为本地接入网或居民接入网。

<br>

1.6计算机网络的性能

    计算机网络的性能指标
    
    1.速率	
    	网络技术中的速率指的是数据的传送速率，也称数据率data rate 或比特率bit rate
    
    2.带宽
    	带宽本来是指某个信号具有的频带宽度，这种意义的带宽单位是赫
    	在计算机网络中，带宽用来表示网络中某通道传输数据的能力，因此网络带宽表示在单位时间内某信道的最高数据率
    
    3.吞吐量
    	表示单位时间内通过某个网络或信道、接口的实际数据量，显然吞吐量受网络额定速率和带宽影响，一般远低于速率
    
    4.时延
    	（1）发送时延 主机或路由器发送数据帧所需要的时间，从数据帧的第一个比特到结束为止，也叫传输时延
    		发送时延 = 数据帧长度(bit)/(bit/s)发送速率
    	
    	（2）传播时延	电磁波在信道中传播一定距离需要花费的时间
    		传播时延 = 信道长度(m)/传播速率(m/s)
    		光速在自由空间：3x10^5km/s，铜线电缆：2.3x10^5km/s, 光纤：2.0x10^5km/s
    		1000km光纤线路传播时延为5ms
    
    	（3）处理时延 主机或路由器收到分组后处理所花费的时间
    	
    	（4）排队时延 分组在进入路由时在输入队列中等待的时间和路由确定转发口后在输出队列中等待时间之和
    	
    	数据在网络中经历的总时延就是以上四种时延之和
    	
    5.时延带宽积	传播时延和带宽相乘 又称以比特为单位的链路的长度
    	只有在代表链路的管道充满比特时，链路才得到充分的利用
    
    6.往返时间RTT (Round-Trip Time) 双向交互一次所需的时间
    	可以通过RTT算出有效数据率
    	有效数据率 = 数据长度/(发送时间+RTT)
    	发送时间指发送方的发送时延，RTT包含网络中所有节点的发送时延、处理时延和排队时延，还有传播时的传播时延
    
    7.利用率
    	（1）信道利用率 某信道有百分之几的时间是被利用(有数据通过)的，完全空闲的信道利用率为0
    	
    	（2）网络利用率 全网络的信道利用率的加权平均值
    		D = D0/(1 - U)
    	D0网络空闲时时延，D网络当前时延，U利用率
    	
    计算机网络的非性能特征
    1.费用
    2.质量
    3.标准化
    4.可靠性
    5.可拓展和可升级性
    6.易于管理和维护

1.7计算机网络体系结构

![计算机网络体系结构](D:\work\Myhub\Note\Picture\计算机网络体系结构.png)

    计算机网络的体系结构是计算机网络的各层及其协议的总和    
    
    开放系统互连基本参考模型 SI/RM (Open Systems Interconnection Reference Model）是法律上的国
    际标准
    OSI 七层协议体系结构的概念清楚，理论也较完整，但它既复杂又不实用
        
    TCP/IP 是事实上的国际标准
    TCP/IP 是一个四层的体系结构，它包含应用层、运输层、网际层和网络接口层（用网际层这个名字
    是强调这一层是为了解决不同网络的互连问题〉。不过从实质上讲， TCP/IP 只有最上面的层，因
    为最下面的网络接口层并没有什么具体内容。
    在学习计算机网络的原理时往往采取折中的办法，即综合 OSI TCP/IP 的优点，采用一种只有五层协
    议的体系结构
    
    W3C（万维网联盟）标准:
    	结构化标准语言（HTML、XML）、表现标准语言(CSS)、行为标准(DOM、ECMScript)
    	
    	1.应用层（application layer）
    	
    		通过特定应用进程间的交互来完成特定网络应用。应用层协议定义的是应用进程间通信和交互的规则。这里进程		 指正在运行的程序。不同的网络应用需要有不同的应用层协议。常见的应用层协议有:DNS、HTTP、SMTP等。
    		我们把应用层交互的数据单元称为报文(message)
    		
    		DNS(Domain Name System)
    		作用是将人类可读的域名 (如，www.example.com) 转换为机器可读的 IP 地址 (如，192.0.2.44)。			DNS协议建立在 UDP 或 TCP 协议之上，默认使用 53 号端口。
    		
    		HTTP(Hyper Text Transfer Protocol)
    		用于从万维网（WWW:World Wide Web ）服务器传输超文本到本地浏览器的传送协议。
    		HTTP是一个基于TCP/IP通信协议来传递数据（HTML 文件, 图片文件, 查询结果等）。
    		HTTP是一个属于应用层的面向对象的协议，由于其简捷、快速的方式，适用于分布式超媒体信息系统。
    	
    	2.运输层(transport layer)
    		
    		向两台主机中进程间的通信提供通用的数据传输服务。应用进程利用该服务传送应用层报文。运输层有复用和分		 用的功能，复用是多个应用层进程可同时使用下面运输层的服务，分用是将收到的信息分别交付给应用层中相应		  的进程。
    		运输层主要采用两种协议：
    		
    		传送控制协议TCP(Transmission Control Protocol)
    			提供面向连接的、可靠的数据传输服务，其数据传输的单位是报文段(segment)
                
            用户数据协议UDP(User Datagram Protocol)
            	提供无连接的、尽最大努力(best-effort)的数据传输服务(不保证可靠性)，其传输单位是用户数据报
        
        3.网络层(network layer)
        
        	负责为分组交换网上的不同主机提供通信服务。在发送数据时，网络层把运输层产生的报文段或用户数据报封装		 成分组或包进行传送。在TCP/IP体系中，由于网络层使用IP协议，因此分组也叫做IP数据报或数据报。
        	
        	网络层的另一任务是选择合适的路由器，使源主机运输层传下来的分组，能够通过网络中的路由器找到目标主机
        	互联网是由大量的异构网络和路由器相互连接起来的。互联网使用的网络层协议是无连接的IP协议(Internet 		  Protocol)和许多种路由选择协议，因此网络层也叫网际层或IP层
        	
        	IP协议配套的三个协议：
        		ARP（Address Resolution Protocol）	地址解析协议
        		ICMP（Internet Control Message Proto）	网际控制报文协议
        		IGMP（Internet Group Management Protocol）	网际组管理协议
        
        4.数据链路层(data link layer)
        
        	数据链路层常简称为链路层。
        	链路层协议有许多种，但有三个基本问题是共通的：1.封装成帧，2.透明传输，3.差错控制
        	
        	相邻两个结点传输数据时，链路层将网络层传下来的IP数据报组装成帧(framing)，每一帧包括数据和必要的		 控制信息（头部SOH和尾部EOT）。控制信息能提取出数据部分上交给网络层，还能检测收到的帧有无差错，有		错就简单的丢弃该错误帧，如果要改正差错则要采用可靠传输协议，这种方法会使链路层的协议复杂一些，内容		 和控制信息冲突则填充转义字符ESC
                	子层：LLC、MAC
    		CRC(循环冗余检验)、FCS(帧检测序
            	子层：LLC、MAC
            	CRC(循环冗余检验)、FCS(帧检测序列)
        	PPP(Point-to-Point-Protocl)
        		目前使用得最广泛的链路层协议
        		PPP的三个部分：
        			将IP数据包封装到串行链路的方法
        			LCP（Link Control Protocl）
        			NCP（Network Control Protocol）
        		PPP协议的帧格式
        			首部(F(7E),A(FF),C(03),协议(2bits))
        			信息部分(IP数据报(<=1500bits))
        			尾部(FCS(2bits), F(7E))
        		不同协议字段对应不同类型的信息部分：
        			0x0021:	IP数据报
        			0X8021：网络控制数据
        			0XC021：PPP链路控制数据
        			0XC023：鉴别数据
        	MAC层帧格式：
        			目的地址（6bit）+ 源地址（6bit） + 类型（2bit） + 数据报（46--1500） + FCS(4bit)
        	CSMA/CD协议：（p85）
        		不能进行全双工通信，通信过程中可能发生碰撞，最先发送帧的站在至多2r（两倍）
        	
        	极限信道利用率计算公式：（p93）
        		Smax = T0/(T0+t) = 1/(1+a)
        	
        5.物理层
        	
        	在物理层上传输的单位是比特。物理层要考虑用多大的电压表示比特，以及接收方如何识别发送方所发送的比		特，还要确定连接电缆的插头应当有多少根引脚以及各引脚如何连接。传递信息所用的一些物理媒介并不在物理		 层协议内而是在物理层协议的下面，也有人把它们称为第零层。
            物理层特性：
                机械特性：指定硬件规格
                电气特性：指明接口电缆的各条线的电压范围
                功能特性：指明某条线上某一电平的电压表示的意义
                过程特性：指明对不同功能的各种可能事件的出现顺序
                
    	6.第零层（物理层下面的传输媒体）
        
            EIA/TIA-568标准:
            T568A的线序：白绿 绿 白橙 蓝 白蓝 橙 白棕 棕
            T568B的线序：白橙 橙 白绿 蓝 白蓝 绿 白棕 棕
            常用T568B线序
    
    网络协议主要由以下三个要素组成
        1.语法， 即数据与控制信息的结构或格式
        2.语义， 即需要发出何种控制信息，完成何种动作以及做出何种响应
        3.同步，即事件实现顺序的详细说明
<br>

​    