## Cookie Session Application

### 1.HTTP 协议

- 无连接性

  - 在一个页面上登录到我的后台了，到另外一个页面，他就不知道我登录没登录。因为他们之间没连着，如何解决这个问题呢？

  - 在客户端记录东西，只允许写文本文档，在客户端阻止服务端往客户端写东西（Cookie）
    - 服务器可以向客户端写内容
    - 只能写文本内容
    - 客户端可以阻止服务器写入
    - 只能拿自己Web application写入的内容，浏览器同源策略
      - 父子域名
      - 跨域
  - Cookie（不可靠）
    - key-value
    - 两周内不用重新输入用户名 -> 一定是记录在Cookie里面了
    - 分类
      - 写在**文件**中，所有窗口中都可看得到**调用setMaxAge()**
      - 写在**内存**里，在本窗口和本窗口的孩子窗口中可以看到，而在新打开得窗口中不可见，**没调用setMaxAge()** 
    - 一个Servlet/JSP设置的Cookie可以被**同一个路径(URL)下面或者子路径下面**的Servlet/JSP读到。

- Session

  - 记录在服务器端的，**服务器端的一块儿内存，与浏览器的窗口或者子窗口**
  - 一个浏览器，一个Session
  - SessionId：浏览器**独一无二**的号码
  - 实现方式
    - Cookie：存到**临时Cookie**就可以了
    - URL重写
  - 规则:
    - 如果浏览器支持Cookie，创建Session的时候会把SessionId写道Cookie中
    - 如果浏览器不支持Cookie, SeesionId每一次刷新都会变(生成新的SessionId)，使用**URL重写方案** 
      - response.encodeURL(): **转码，URL后面加入SessionID**，**每个链接**都要加这句话
      - 访问的时候把sessionID传给我
      - Session是与窗口关联在一起的
    - Session不像Cookie, 有目录的问题，有路径访问的问题，同一个application下的servlet/jsp可共享同一个Session，前提是**同一个客户端窗口** 

- Application

  - 网页浏览次数的值记录

- JSP九大对象

| 内置对象名  | 类型                |
| ----------- | ------------------- |
| request     | HttpServletRequest  |
| response    | HttpServletResponse |
| config      | ServletConfig       |
| application | ServletContext      |
| session     | HttpSession         |
| exception   | Throwable           |
| page        | Object(this)        |
| out         | JspWriter           |
| pageContext | PageContext         |

- 过滤器
- 监听器
- [源代码](<https://github.com/MarkShen1992/Learn-Servlet>) 

---

[back2index](./../../index.html)