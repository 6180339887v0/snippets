## 前排劝退
**不回答“怎么用”这种问题，建议用其他人方便易用的代码。CF代理基础知识建议到CM佬群学习。**  
**无前端，无订阅，专注代理本身：极致直连 + 多落地协议。**  
**订阅功能可自行搭配 [EDT](https://github.com/cmliu/edgetunnel) 或订阅器实现。**  
**仅适合对CF节点有一定基础的同学，至少得会用节点模板修改节点信息。**  

---
## 文件说明
* **snippet.js：** ws/xhttp 双传输，vless/trojan/ss 三协议，支持 `!txt + socks5 + http + https + sstp + turn` 功能，此 https 非完全体。  
* **worker.js：** ws/xhttp 双传输，vless/trojan/ss 三协议，支持 `!txt + socks5 + http + https + sstp + turn + turns` 功能，此 https 为完全体。  
* **!txt+https.js：** ws/xhttp 双传输，vless/ss 双协议，支持 `!txt + https` 功能，此 https 为完全体。  

_建议：ss 用 notls。_  
_注1：ss 单 ws，无 xhttp。_  
_注2：据说5片段免费 snippet 用不了 xhttp，没有，无从测试，自测。_  
_注3：代码验证基于 Pro计划 snippet，worker free。_  

---
## 功能说明
1. **!txt：** 通过后缀标记 `!txt` 支持采用 TXT 记录的域名，TXT 记录值为 proxyip 或 socks5 等协议代理，比如威廉维护的 [*.william.us.ci!txt](https://t.me/CMLiussss_channel/84)（点击跳转获取）。普通 A 记录的并不需要加 !txt，如 CM佬的。  
2. **socks：** 略  
3. **http：** 略  
4. **https：** 完全体支持 `https://domain:port` 和 `https://ip:port`，ip 直接走 TlsClient，带 `!ip` 后缀标记强制走 TlsClient；非完全体仅支持 `https://domain:port`，见 [AK说明](https://t.me/Enkelte_notif/817)  
5. **sstp：** 小日子大学的个人志愿者公益家宽，见 [AK说明](https://t.me/Enkelte_notif/819)  
6. **turn：** 见 [AK说明](https://t.me/Enkelte_notif/805)  
7. **turns：** turn over tls，与 https 代理情况类似。  
8. **global：** 协议代理（socks5等）默认回落模式，?global=1 时改用全局模式。  
9. **colo：** CM佬的自适应反代服务，自动根据当前位置分配 proxyip，path > colo > n。  

**总结**：这些功能解决的是CF节点的落地问题，助力实现**无限家宽全球落地**。  
**另注**：TXT 内容格式以 `,` 分隔或换行或两者混用。作用逻辑：获取域名 TXT 记录内容，取其中某个 proxyip 或协议代理使用。  

### 路径示例
1. **!txt：**  
`/fdip=domain!txt?ed=2560`
2. **socks：**  
`/fdip=socks5://host:port?ed=2560`
3. **http：**  
`/fdip=http://host:port?ed=2560`
4. **https：**  
`/fdip=https://domain:port?ed=2560`
`/fdip=https://ip:port?ed=2560`
`/fdip=https://host:port!ip?ed=2560`
5. **sstp：**  
`/fdip=sstp://host:port?ed=2560`
6. **turn：**  
`/fdip=turn://host:port?ed=2560`
7. **turns：**  
`/fdip=turns://domain:port?ed=2560`
`/fdip=turns://ip:port?ed=2560`
`/fdip=turns://host:port!ip?ed=2560`
8. **global：**  
`/fdip={1234567}?global=1&ed=2560`
9. **colo：**  
`/?colo=1&ed=2560`

_注1：ed=2560 放在最后_  
_注2：fdip 可以改为任意数字字母组合如 proxyip_  

### 节点示例
**Vless**
```ws
vless://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?path=%2Ffdip%3D1.2.3.4%3A443%3Fed%3D2560&security=tls&encryption=none&insecure=0&host=vless.snippets.cf&fp=chrome&type=ws&allowInsecure=0&sni=vless.snippets.cf#ws
```
```xhttp
vless://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?mode=stream-one&path=%2Ffdip%3D1.2.3.4%3A443%3Fed%3D2560&security=tls&alpn=h2&encryption=none&insecure=0&host=vless.snippets.cf&fp=chrome&type=xhttp&allowInsecure=0&sni=vless.snippets.cf#xhttp
```
**Trojan**
```ws
trojan://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?path=%2Ffdip%3D1.2.3.4.%3A443%3Fed%3D2560&security=tls&insecure=0&host=trojan.snippet.cf&fp=chrome&type=ws&allowInsecure=0&sni=trojan.snippet.cf#ws
```
```xhttp
trojan://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?mode=stream-one&path=%2Ffdip%3D1.2.3.4.%3A443%3Fed%3D2560&security=tls&alpn=h2&insecure=0&host=trojan.snippet.cf&fp=chrome&type=xhttp&allowInsecure=0&sni=trojan.snippet.cf#xhttp
```
**SS(notls)**
```ws
ss://YWVzLTEyOC1nY206NDk1YzcxOTUtODViOC00OThhLWJmMjAtMmVhOWNlOTE3NWI1@www.shopify.com:80?plugin=v2ray-plugin%3Bmode%3Dwebsocket%3Bhost%3Dss.snippets.cf%3Bpath%3D%2Ffdip%3D1.2.3.4%3A443%3Fed%3D2560%3Bmux%3D0#ws
```

---
## 特别提醒
**若1101请全删旧片段再部署，已有正常运行中的片段需谨慎，部署新片段会触发全部片段代码检测。**  
**有问题请开 issue 或联系 [tg bot](https://t.me/meindmBot) 直奔主题，欢迎反馈，欢迎 PR。**  

---
## 鸣谢
**[AK](https://github.com/ToiCF)、[CM](https://github.com/cmliu)、AI**
