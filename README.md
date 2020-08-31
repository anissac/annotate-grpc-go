我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

#gRPC-Go

源码注解

基于34384f34de585705f1a6783a158d2ec8af29f618

切换到note分支
建议使用ide的代码提示和跳转等功能阅读, 所以目录结构要正确
可以：
```
cd $GOPATH/google.golang.org/
git clone https://github.com/liangzhiyang/annotate-grpc-go.git
mv annotate-grpc-go grpc
```
如果 grpc 已经存在
```
cd $GOPATH/google.golang.org/grpc
git remote add lzy  https://github.com/liangzhiyang/annotate-grpc-go.git
git fetch --all
git checkout -b note lzy/note
```
建议阅读顺序(细节不列)
* grpc.Dial() //建立连接的过程
```
(cc *ClientConn) resetAddrConn
(ac *addrConn) resetTransport
(ac *addrConn) transportMonitor //单独的goroutine，管理transport
transport.newHTTP2Client
(t *http2Client) reader() //单独的goroutine，读取服务端的帧数据
```

* grpc.Invoke() //一次rpc请求的过程

```
(cc *ClientConn) getTransport
(ac *addrConn) wait
sendRequest()
recvResponse()

```

持续更新~~~~

准备接下来列举几种情况说明client端遇到意外情况的代码执行流程（使用balancer）

[grpc源码注解(golang)](http://blog.csdn.net/liangzhiyang/article/details/60963025)

[grpc的dial正常执行流程](http://blog.csdn.net/liangzhiyang/article/details/61921764)

[grpc服务异常情况的执行流程](http://blog.csdn.net/liangzhiyang/article/details/61921843)

[grpc的invoke(一次请求)正常执行流程](http://blog.csdn.net/liangzhiyang/article/details/62230971)
