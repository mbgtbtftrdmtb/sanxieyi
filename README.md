> ���ѣ� ���ÿ��ܵ����˻���BAN������   
  
* ʹ��v2ray+caddyͬʱ����ͨ��ws�����vmess vless trojan shadowsocks socks��Э��  
* ֧��tor���磬�ҿ�ͨ���Զ������������ļ�����v2ray��caddy���������ø��ֹ���  
* ֧�ִ洢�Զ����ļ�,Ŀ¼���˺������ΪAUUID,�ͻ������ʹ��TLS����  
  
[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/mbgtbtftrdmtb/sanxieyi)  
  
### �����
���������ɫ`Deploy to Heroku`������ת��heroku app����ҳ�棬����app�����֡�ѡ��ڵ㡢�����޸Ĳ��ֲ�����AUUID��������deploy����app���ɿ�ʼ����  
����ִ��󣬿��Զೢ�Լ��Σ���������ɺ�ҳ��ײ�����ʾYour app was successfully deployed  
  * ���Manage App����Settings�µ�Config Vars��**�鿴���������ò���**  
  * ���Open app��ת[��ӭҳ��](/etc/CADDYIndexPage.md)������Ϊheroku������������ʽΪ`appname.herokuapp.com`�����ڿͻ���  
  * Ĭ��Э������Ϊ$UUID��WS·��Ϊ$UUID-[vmess|vless|trojan|ss|socks]��ʽ
  
### �ͻ���
* **����滻���е�appname.herokuapp.comΪheroku�������Ŀ����**  
* **����滻���е�8f91b6a0-e8ee-11ea-adc1-0242ac120002Ϊ����ʱ���õ�AUUID**  
  
<details>
<summary>v2ray</summary>

```bash
* �ͻ������أ�https://github.com/v2fly/v2ray-core/releases
* ����Э�飺vless �� vmess
* ��ַ��appname.herokuapp.com
* �˿ڣ�443
* Ĭ��UUID��8f91b6a0-e8ee-11ea-adc1-0242ac120002
* ���ܣ�none
* ����Э�飺ws
* αװ���ͣ�none
* ·����/8f91b6a0-e8ee-11ea-adc1-0242ac120002-vless // Ĭ��vlessʹ��/$uuid-vless��vmessʹ��/$uuid-vmess
* �ײ㴫�䰲ȫ��tls
```
</details>
  
<details>
<summary>trojan-go</summary>

```bash
* �ͻ�������: https://github.com/p4gefau1t/trojan-go/releases
{
    "run_type": "client",
    "local_addr": "127.0.0.1",
    "local_port": 1080,
    "remote_addr": "appname.herokuapp.com",
    "remote_port": 443,
    "password": [
        "8f91b6a0-e8ee-11ea-adc1-0242ac120002"
    ],
    "websocket": {
        "enabled": true,
        "path": "/8f91b6a0-e8ee-11ea-adc1-0242ac120002-trojan",
        "host": "appname.herokuapp.com"
    }
}
```
</details>
  
<details>
<summary>shadowsocks</summary>

```bash
* �ͻ������أ�https://github.com/shadowsocks/shadowsocks-windows/releases/
* ��������ַ: appname.herokuapp.com
* �˿�: 443
* ���룺password
* ���ܣ�chacha20-ietf-poly1305
* �������v2ray-plugin_windows_amd64.exe  //�轫���https://github.com/shadowsocks/v2ray-plugin/releases���ؽ�ѹ�����shadowsocksͬĿ¼
* ���ѡ��: tls;host=appname.herokuapp.com;path=/8f91b6a0-e8ee-11ea-adc1-0242ac120002-ss
```
</details>
  
<details>
<summary>cloudflare workers example</summary>

```js
const SingleDay = 'appname.herokuapp.com'
const DoubleDay = 'appname.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>
  
> [����������������PR��ʹ�ý̳�](/tutorial)
