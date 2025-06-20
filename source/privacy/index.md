## 更新日期

本协议的最近更新日期为：2024-10-20

本站非常重视用户的隐私和个人信息保护。你在使用网站时，可能会收集和使用你的相关信息。通过《隐私政策》向你说明在你访问 `blog.coul.top`网站时，如何收集、使用、保存、共享和转让这些信息。

## 最新更新时间

协议最新更新时间为：2024-11-15

## 一、在访问时如何收集和使用你的个人信息

### 在访问时，收集访问信息的服务会收集不限于以下信息：

**网络身份标识信息**（浏览器 UA、IP 地址）

**设备信息**

**浏览过程**操作方式、浏览方式与时长、性能与网络加载情况）。

### 在访问时，本站内置的第三方服务会通过以下或更多途径，来获取你的以下或更多信息：

- **百度统计工具** 会收集你的访问信息、访问操作过程
- **umami 统计工具** 会收集你的访问信息
- **umami/up监控平台** 会收集你的访问操作过程和资源加载情况
- **今日头条搜索** 会收集你的访问信息
- **字节跳动静态资源库** 会收集你的访问信息
- **Tianlicdn** 会收集你的访问信息
- **busuanzi 统计** 会收集你的访问信息
- **腾讯云** 会收集你的访问信息
- **腾讯 Codesign** 会收集你的访问信息
- **阿里 cdn（iconfont）** 会收集你的访问信息
- **QQ 音乐** 会收集你的访问信息
- **网易云 音乐** 会收集你的访问信息

### 在访问时，本人仅会处于以下目的，使用你的个人信息：

- 用于网站的优化与文章分类，用户优化文章
- 恶意访问识别，用于维护网站
- 恶意攻击排查，用于维护网站
- 网站点击情况监测，用于优化网站页面
- 网站加载情况监测，用于优化网站性能
- 用于网站搜索结果优化
- 浏览数据的展示

### 第三方信息获取方将您的数据用于以下用途：

第三方可能会用于其他目的，详情请访问对应第三方服务提供的隐私协议。

### 你应该知道在你访问的时候不限于以下信息会被第三方获取并使用：

第三方部分为了抵抗攻击、使用不同节点 cdn 加速等需求会收集不限于以下信息

<!-- 在表格中添加 id 以便于通过 JavaScript 获取元素 -->
<table>
  <thead>
    <tr>
      <th>类型</th>
      <th>信息</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="2"><b>网络信息</b></td>
    </tr>
    <tr>
      <td>IP地址</td>
      <td><div id="userAgentIp"></div></td>
    </tr>
    <tr>
      <td>国家</td>
      <td><div id="userAgentCountry"></div></td>
    </tr>
    <tr>
      <td>省份</td>
      <td><div id="userAgentProv"></div></td>
    </tr>
    <tr>
      <td>城市</td>
      <td><div id="userAgentCity"></div></td>
    </tr>
    <tr>
      <td>运营商</td>
      <td><div id="userAgentISP"></div></td>
    </tr>
    <tr>
      <td colspan="2"><b>设备信息</b></td>
    </tr>
    <tr>
      <td>操作系统</td>
      <td><div id="userAgentOS"></div></td>
    </tr>
    <tr>
      <td>浏览器</td>
      <td><div id="userAgentBrowser"></div></td>
    </tr>
  </tbody>
</table>

此页面如果未能获取到信息并不代表无法读取上述信息，以实际情况为准。此页面获取地址信息展示使用的是[青桔](https://api.76.al)提供的API。
<!-- 在模板文件中添加 JavaScript 代码 -->
<script>
    // 获取ip
    function getIpInfo(){
        var fetchUrl = "https://api.76.al/api/ipv4/query?key=Iiikw1HEG6N6DRU3uMpepwcJfY"  //key申请：https://api.76.al
        fetch(fetchUrl)
        .then(res => res.json())
        .then(json =>{
            var country = json.data.country || "未能获取到信息";
            var ip = json.data.ip || "未能获取到信息";
            var province = json.data.province || "未能获取到信息";
            var city = json.data.city || "未能获取到信息";
            var districts = json.data.districts || "未能获取到信息"
            var isp = json.data.isp || "未能获取到信息";
    
            document.getElementById("userAgentIp").innerHTML = ip;
            document.getElementById("userAgentCountry").innerHTML = country;
            document.getElementById("userAgentProv").innerHTML = province;
            document.getElementById("userAgentCity").innerHTML = city;
            document.getElementById("userAgentISP").innerHTML = isp;
    
            // 使用ua-parser-js解析User-Agent
            var parser = new UAParser();
            var result = parser.getResult();
            document.getElementById("userAgentOS").innerHTML = result.os.name + " " + result.os.version;
            document.getElementById("userAgentBrowser").innerHTML = result.browser.name + " " + result.browser.version;
        })
    }
    
    getIpInfo()
</script>

<script src="privacy.js"></script>
<script src="https://cdn.jsdelivr.net/npm/ua-parser-js@0.7.14/dist/ua-parser.min.js"></script>

## 二、在评论时如何收集和使用你的个人信息

评论使用的是无登陆系统的匿名评论系统，你可以自愿填写真实的、或者虚假的信息作为你评论的展示信息。

`鼓励你使用不易被人恶意识别的昵称进行评论`，但是建议你填写`真实的邮箱`以便收到回复（邮箱信息不会被公开）。

在你评论时，会额外收集你的个人信息。

### 在评论时，本站内置的第三方服务会通过以下或更多途径，来获取你的相关信息：

- `cravatar` 会收集你的访问信息、评论填写的个人信息用于展示头像

### 在访问时，本人仅会处于以下目的，收集并使用以下信息：

- 评论时会记录你的 QQ 账号（如果在邮箱位置填写 QQ 邮箱或 QQ 号），方便获取你的 QQ 头像。如果使用 QQ 邮箱但不想展示 QQ
  头像，可以填写不含 QQ 号的 QQ 邮箱。（主动，存储）
- 评论时会记录你的邮箱，当我回复后会通过邮件通知你（主动，存储，不会公开邮箱）
- 评论时会记录你的网址，用于点击头像时快速进入你的网站（主动，存储）
- 评论时会记录你的 IP 地址，作为反垃圾的用户判别依据（被动，存储，不会公开 IP，会公开 IP 所在城市）
- 评论会记录你的浏览器代理，用作展示系统版本、浏览器版本方便展示你使用的设备，快速定位问题（被动，存储）

## 三、如何使用-Cookies-和本地-LocalStorage-存储

本站为实现无账号评论、深色模式切换，不蒜子的 uv 统计等功能，会在你的浏览器中进行本地存储，你可以随时清除浏览器中保存的所有
Cookies 以及 LocalStorage，不影响你的正常使用。

本博客中的以下业务会在你的计算机上主动存储数据：

`内置服务`

- 评论系统
- 即刻短文
- 鱼塘
- 中控台
- 胶囊音乐

`第三方服务`

- 百度统计
- busuanzi 统计

关于如何使用你的 Cookies，请访问 [Cookies 政策](https://blog.coul.top/cookies/)。

关于如何[在 Chrome 中清除、启用和管理 Cookie](https://support.google.com/chrome/answer/95647?co=GENIE.Platform=Desktop&hl=zh-Hans)。

## 四、如何共享、转让你的个人信息

本人不会与任何公司、组织和个人共享你的隐私信息

本人不会将你的个人信息转让给任何公司、组织和个人

第三方服务的共享、转让情况详见对应服务的隐私协议

## 五、附属协议

当监测到存在恶意访问、恶意请求、恶意攻击、恶意评论的行为时，为了防止增大受害范围，可能会临时将你的 ip
地址及访问信息短期内添加到黑名单，短期内禁止访问。

此黑名单可能被公开，并共享给其他站点（主体并非本人）使用，包括但不限于：IP 地址、设备信息、地理位置。