# DNSMASQ 是个好东东

## 安装

手动跳过

## 配置

```
# vim /etc/dnsmasq.conf
listen-address=127.0.0.1
server=/company.com/10.0.0.1
address=/double-click.net/127.0.0.1
resolv-file=/etc/resolv.dnsmasq.conf
```

解释一下每行的意思：

* server=/company.com/10.0.0.1

    意思是用 DNS Server `10.0.0.1` 来解析`company.com`相关的域名。很多公司都有自己的 DNS Server 并解析公司内部域名和外部域名，这个 DNS Server 和公共 DNS Server 相比起来太弱了，没法分域解析一些较大网站的域名，比如我们公司是电信网，却把百度解析到了联通上面，导致网速变慢。

* address=/double-click.net/127.0.0.1

    意思是将`double-click.net`解析到`127.0.0.1`上面，这是正则匹配的，比`/etc/hosts`文件强大多了。

* resolv-file=/etc/resolv.dnsmasq.conf

    DNSMasq 默认会去`/etc/resolv.conf`里找 DNS Server ，我们要让它从`/etc/resolv.dnsmasq.conf`里找，这里定义公共的 DNS Server ，比如阿里的`223.5.5.5`和`223.6.6.6`，而`/etc/resolv.conf`里的 DNS Server 写`127.0.0.1`。


## Ubuntu 下的配置

请参考这里: [ubuntu/dnsmasq.md](../ubuntu/dnsmasq.md)

<!--
## Mac OSX

```
$ brew install dnsmasq
$ cp /usr/local/opt/dnsmasq/dnsmasq.conf.example /usr/local/etc/dnsmasq.conf
$ vim /usr/local/etc/dnsmasq.conf
$ sudo cp -fv /usr/local/opt/dnsmasq/*.plist /Library/LaunchDaemons
$ sudo chown root /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist
$ sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist # use unload to stop
```
-->