> # 特别注意事项：**不要在国内媒体平台宣传danmu_api**

# 这是一份非官方的[danmu_api](https://github.com/huangxd-/danmu_api)搭建教程，

## 是否有必要搭建弹幕API

目前danmu_api支持 forward/senplayer/hills/小幻/yamby/eplayerx/afusekt/uz影视/dscloud/lenna/danmaku-anywhere/omnibox 等播放器。

搭配danmaku-anywhere可以实现为你的网页播放器提供好用的弹幕服务

> [danmaku-anywhere](https://github.com/Mr-Quin/danmaku-anywhere)旨在为你喜爱的几乎任何视频网站添加弹幕。通过添加自定义弹幕API例如danmu_api，可使用该插件为你的网页播放器提供弹幕。

## 最推荐的部署平台是Vercel和Netlify 【稳定，个人使用不会超额】

### 以下教程以Vercel为例

> ### [vercel部署及自动更新教程](https://github.com/xiaoyao20084321/log-var-danmu-deployment-guide)

> ### 优化点

* Settings > Functions > Advanced Setting > Function Region 切换为 新加坡/韩国/日本等，能提高访问速度，体验更优
  
  > hk 有可能访问不了 360 或其他源，可以尝试切其他 region
* vercel 在国内被墙，请配合代理或绑定自定义域名使用
  
  > 非必要教程-[使用 Vercel 搭建万能反向代理，部署后请绑定自定义域名使用](https://github.com/souying/vercel-api-proxy)

**推荐**：使用站内佬的edu.deal域名或者买一个xyz域名挂载到cloudflare，单域名SaaS优选再绑定

## 启用热更新

在Vercel中需设置变量：

**ADMIN\_TOKEN**    用于更改**系统变量**，消除日志等，自行设置
**DEPLOY\_PLATFROM\_PROJECT**
**DEPLOY\_PLATFROM\_TOKEN**

> **DEPLOY变量**可查看官方文档获取变量值——[各平台变量获取详细步骤](https://github.com/huangxd-/danmu_api/blob/main/danmu_api/ui/README.md#%E5%90%84%E5%B9%B3%E5%8F%B0%E5%8F%98%E9%87%8F%E8%8E%B7%E5%8F%96%E8%AF%A6%E7%BB%86%E6%AD%A5%E9%AA%A4)

访问域名/ADMIN\_TOKEN 进行下一步的变量设置 **例如**：https://danmu.8081666.xyz/ADMIN_TOKEN

## UI界面变量设置
![图片|690x431, 100%](upload://remUpyTJOJ6bYOFiu41KjEZBVH5.jpeg)

可查看官方的-[环境变量列表](https://github.com/huangxd-/danmu_api/tree/main#%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E5%88%97%E8%A1%A8)

### 1.API配置：

**TOKEN**  用于**调用API**，须在链接后填入**TOKEN**才可使用 **例如**：https://danmu.8081666.xyz/TOKEN

**RATE\_LIMIT\_MAX\_REQUESTS**  限流配置：**同一IP**内1 分钟内最大请求次数


### 2.源配置

**SOURCE\_ORDER**  采集源设置，推荐设置为`douban,renren,hanjutv,dandan,vod`

**douban**反应速度快，返回弹幕多，**360**或**vod**这类资源比较杂用于兜底，**renren**用于美剧，**hanjutv**用于韩剧，**dandan**用于动漫。~~TMDB和哈姆雷特~~没试过




> 当启用**B站**需设置**BILIBILI\_COOKIE**，**有封号风险**

[采集源及对应平台列表](https://github.com/huangxd-/danmu_api/tree/main?tab=readme-ov-file#%E9%87%87%E9%9B%86%E6%BA%90%E5%8F%8A%E5%AF%B9%E5%BA%94%E5%B9%B3%E5%8F%B0%E5%88%97%E8%A1%A8)

**VOD\_SERVERS** 默认即可，通常追风返回速度是最快的

**VOD\_RETURN\_MODE** VOD 返回模式：**all**（所有站点）或 **fastest**（最快的站点），默认 **fastest** 

**VOD\_REQUEST\_TIMEOUT** 当采集源**SOURCE\_ORDER**启用**VOD**需设置，默认10S，建议调整为**15S**以上

> 非必要 **BILIBILI\_COOKIE** 可自行设置，参考[环境变量列表](https://github.com/huangxd-/danmu_api/tree/main#%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E5%88%97%E8%A1%A8)

### 3.匹配设置

**PLATFORM\_ORDER** 优先匹配排名靠前的，适用于**自动匹配**和**手动匹配**，根据个人来调整，推荐设置为`qiyi,qq,youku,bilibili1,imgo,dandan,renren,hanjutv`

### 4.弹幕设置

**BLOCKED\_WORDS** 屏蔽词，自行设置，可能降低弹幕返回速度，建议在播放器里设置

**GROUP\_MINUTE** 分钟内合并去重（0 表示不去重），默认 1

### 5.缓存配置

数据库＞内存 ，优先存储在数据库中，非必须配置数据库

### 6.系统设置

**LOG\_LEVEL**  默认日志储存在内存中，可以手动清理日志。

> 日志级别，默认为 `info`，可选值：`error`（仅错误）、`warn`（错误和警告）、`info`（所有日志），生产环境建议使用 `warn`，调试时使用 `info`

## 别忘了点击重新部署

#### 一般播放器设置自定义弹幕API 例如：https://danmu.8081666.xyz/TOKEN 即可

## 教程到这里完毕

PS:如果你懒得部署，可以直接用我分享的弹幕API。只不过报错多一点，慢一点。。。。

[自建弹幕API](https://linux.do/t/topic/1306277)
