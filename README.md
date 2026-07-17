## 前排劝退
**无前端，无订阅，专注代理本身：极致直连 + 多落地协议。**  
**订阅功能可自行搭配 [EDT](https://github.com/cmliu/edgetunnel) 或订阅器实现。**  
**仅适合对CF节点有一定基础的同学，至少得会用节点模板修改节点信息。**  

---
## 文件说明
* **snippet.js**：vless/trojan/shadowsocks 三协议，支持 `!txt` + `socks5` + `http` + `https` + `sstp` + `turn` 功能，此 https 非完全体。  
* **worker.js**：vless/trojan/shadowsocks 三协议，支持 `!txt` + `socks5` + `http` + `https` + `sstp` + `turn` 功能，此 https 为完全体。  
* **!txt+https.js**：vless 单协议，支持 `!txt` + `https` 功能，此 https 为完全体。  

_注1：ss 建议用 notls。_  
_注2：concur取值：pro计划取1（默认），business计划可取2。_  

---
## 功能说明
1. **!txt**：通过标记 `!txt` 支持采用 TXT 记录的反代域名、https等协议代理域名，比如威廉维护的反代域名 [*.william.us.ci!txt](https://t.me/CMLiussss_channel/84)、https://https.example.com!txt  
2. **socks**：略  
3. **http**：略  
4. **https**：完全体支持 `https://host:port` 和 `https://ip:port!ip`，非完全体仅支持 `https://host:port`，见 [AK说明](https://t.me/Enkelte_notif/817)  
5. **sstp**：小日子大学的个人志愿者公益家宽，见 [AK说明](https://t.me/Enkelte_notif/819)  
6. **turn**：见 [AK说明](https://t.me/Enkelte_notif/805)  
7. **global**：协议代理（socks5等）默认全局模式，?global=0 时改用回落模式。  

**总结**：这些功能解决的是CF节点的落地问题，可以实现**无限家宽全球落地**。  
**另注**：TXT 内容格式以 `,` 分隔或换行或两者混用。作用逻辑：获取域名 TXT 记录内容，取其中某个反代 ip:port 或协议代理如 sstp://host:port 使用。  

**路径示例：**
```
1. !txt：
/fdip=*.william.us.ci!txt?ed=2560
/fdip={any}://https.example.com!txt?ed=2560
2. socks：
/fdip=socks5://host:port?ed=2560
3. http：
/fdip=http://host:port?ed=2560
4. https：
/fdip=https://domain:port?ed=2560
/fdip=https://ip:port!ip?ed=2560
5. sstp：
/fdip=sstp://host:port?ed=2560
6. turn：
/fdip=turn://host:port?ed=2560
7. global:
/fdip={23456}?global=0&ed=2560
```
_注意：ed=2560 放在最后_  

**节点示例：**

```vless
vless://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?path=%2Ffdip%3Dhttps%3A%2F%2F1.2.3.4%3A443%21ip%3Fed%3D2560&security=tls&encryption=none&insecure=0&host=https.snippets.cf&fp=random&type=ws&allowInsecure=0&sni=https.snippets.cf#https
```
```trojan
trojan://495c7195-85b8-498a-bf20-2ea9ce9175b5@www.shopify.com:443?path=%2Ffdip%3Dsstp%3A%2F%2Fsstp.example.com%21txt%3Fed%3D2560&security=tls&insecure=0&host=trojan.snippet.cf&fp=chrome&type=ws&allowInsecure=0&sni=trojan.snippet.cf#sstp%21txt
```
```ss(notls)
ss://YWVzLTEyOC1nY206bWltYTIzMzM@cmin2.pjq.cc.cd:80?plugin=v2ray-plugin%3Bmode%3Dwebsocket%3Bhost%3Dsnippets.example.cf%3Bpath%3D%2Ffdip%3Dtw.william.us.ci%21txt%3Fenc%3Daes-128-gcm%26ed%3D2560%3Bmux%3D0#ss_notls
```

---
## 特别提醒
**若1101请全删旧片段再部署，已有正常运行中的片段需谨慎，部署新片段会触发全部片段代码检测。**  
**有问题请开 issue 或联系 [tg bot](https://t.me/meindmBot) 直奔主题**  

---
## 鸣谢
**[老王](https://github.com/eooce/Cloudflare-proxy)、[CM](https://github.com/cmliu/edgetunnel)、[AK](https://github.com/ToiCF)、AI**
