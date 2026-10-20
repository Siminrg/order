# 情侣点单 H5（完全免费版）

一个单文件网页，对方打开链接选菜，你微信收到推送。**零服务器、零备案、零月费。**

---

## 第一步：拿 Server酱 SendKey（2 分钟）

1. 打开 https://sct.ftqq.com/
2. 点「微信扫码登录」，用你自己的微信扫
3. 登录后首页就能看到你的 **SENDKEY**，复制下来

## 第二步：填进网页

用记事本打开 `index.html`，找到这两行（在文件靠前位置）：

```js
const SEND_KEY = 'REPLACE_WITH_YOUR_SERVERCHAN_KEY';
const ORDER_FROM_NAME = '宝宝';
```

- 把 `REPLACE_WITH_YOUR_SERVERCHAN_KEY` 换成你刚复制的 SendKey
- `ORDER_FROM_NAME` 改成你对象对你的称呼（推送消息里会显示"宝宝点了 3 道菜"）

想改菜单？往下翻找到 `const MENU = [...]` 那个数组，自己增删菜品就行，格式照抄。

## 第三步：把网页发到网上（免费）

微信里不能直接发 HTML 文件，得托管成一个链接。最简单的方式：

**用 Netlify Drop（推荐，30 秒搞定）：**
1. 打开 https://app.netlify.com/drop
2. 把整个 `order-h5` 文件夹（或者直接把 `index.html` 文件）拖到网页中间那个虚线框里
3. 它会自动给你一个链接，形如 `https://random-name-123.netlify.app`
4. 这个链接就是你的点单页面

**备选：Vercel**
1. 打开 https://vercel.com/
2. 用 GitHub 账号登录
3. 把 index.html 拖进去部署

## 第四步：发给对象

把 Netlify 给你的链接直接微信发给对象，她点开就能选菜下单。
她点「提交订单」后，你微信会收到 Server酱推送的消息，里面写着她点了什么、合计多少钱、有没有备注。

---

## 自定义菜单

打开 `index.html`，找到这段：

```js
const MENU = [
  { name: '番茄炒蛋',   cat: '热菜', price: 12, desc: '酸甜可口，下饭神器' },
  { name: '红烧肉',     cat: '热菜', price: 28, desc: '肥而不腻，入口即化' },
  ...
];
```

照着格式加菜就行：
- `name`：菜名
- `cat`：分类（热菜/凉菜/汤品/主食/饮品，随便起）
- `price`：价格（数字）
- `desc`：一句话描述

改完保存，重新拖到 Netlify 部署一次就更新了。

## 注意事项

- Server酱免费版每天 5 条推送，情侣一天点两三单够用
- 菜单是写死在页面里的，改菜单 = 改 HTML 重新部署
- 没有"订单历史"页面，你收到的微信推送就是订单记录
- 手机浏览器打开链接就是 App 样子，可以"添加到主屏幕"当 App 用
