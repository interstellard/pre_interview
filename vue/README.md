# 前端Vue.js web app开发面试题

我们希望你能独立地在1.5小时内完成题目任务。结束后给 hr@simplylab.xyz 发送题目的解答，邮件主题请用如下的命名规则：**投递的简历平台+面试岗位+姓名+微信+电话**。

## 该题目的解答提交形式

- 注册GitHub账号，把代码上传到GitHub，直接发送GitHub项目链接给我们
- GitHub上需要有说明文档，写明详细步骤说明，让我们可以本地运行测试你的web app各项功能
- 链接可发送至上述邮箱（hr@simplylab.xyz）

## 题目要求

#### 请使用以下技术/packages完成本题目：
- [Vue.js](https://vuejs.org/)
  - 请使用 Vue 3，从0到1搭建一个全新的项目
- [Vuetify](https://vuetifyjs.com/)

#### 开发过程中，需要满足以下要求：
- 所有的style都请尽量用[Vuetify](https://vuetifyjs.com/)组建完成
- 项目名称为“BestSearch”，整个项目能在本地服务器直接运行
- 页面需要美观、流畅,UI的还原度尽量做到最高
- 提交的web app需要为自适应（responsive design/响应式设计）
- 完成题目的过程中请注意代码、命名规范以及合理的代码注释

在完成项目的过程中，如果你觉得需要安装其他的packages（第三方的包/库)来完成某些功能，请随意安装，方法不限。只要能按以上要求实现web app即可。

## 题目内容具体要求说明

需要搭建的web app一共有两个页面：
- (A) 首页
- (B) 搜索页

其中以下的每个页面顶部都有一个导航栏，位置一直在网页最顶端，不随页面其他内容部分滑动。最左端显示一个网页Logo，名字为BestSearch，其中Best部分字体是加粗的。在任何一个网页点击这个BestSearch都会回到首页。

需要实现的整个web app的demo可以点击这个链接观看：[web app demo](https://preinterview.s3.us-west-2.amazonaws.com/demo.mov)

每个页面的具体细节描述如下：

#### (A) 首页

###### 网页的本地URL：
http://localhost:3000/

###### 功能描述：
用户可以通过（1）按回车键或者（2）点击右方搜索按钮这两种不同的方式触发搜索功能，从而跳转至搜索页 http://localhost:3000/search/{keyword} 进行搜索并显示搜索结果。

###### UI如下图所示：

![home page](https://preinterview.s3.us-west-2.amazonaws.com/preinterview-frontend-1.png?raw=true)


#### (B) 搜索页

###### 网页的本地URL：
http://localhost:3000/search/{keyword}

其中`{keyword}`是当前用户用来搜索的搜索词。

请注意，路径中的`{keyword}`如果包含空格符号，需要转化为 `+` 显示在路径中。

比如如果用户希望搜索`Best cat toys`这个词，那么路径应为 http://localhost:3000/search/Best+cat+toys

###### 功能描述：
在搜索页的导航栏中的搜索框里会显示目前正在搜索的关键词。

在前端网页调用API得到搜索结果之前，显示loading状态。

当前端网页得到后台返回的结果之后，会将搜索结果展现在此搜索页上。

搜索结果内容：
- 标题：Related product trends
- 搜索结果：用responsive layout grid显示后台返回的结果列表

请周全考虑各种不同的进入此页面的情形，并自行做出适当处理。

###### loading状态UI如下图所示：

![search loading page](https://preinterview.s3.us-west-2.amazonaws.com/web_app_search_loading.png?raw=true)

###### 搜索页结果UI如下图所示：

![search results page](https://preinterview.s3.us-west-2.amazonaws.com/web_app_search_results.png?raw=true)

## Web app开发要求说明

如上图所示，本题需要制作一个web app来完成一个简单的搜索动作。页面需要美观、流畅。

- 请调用此接口来获取搜索结果：API: http://3.141.23.218:5000/interview/keyword_search

  Parameters（输入参数）:
```

  {
    "login_token":"INTERVIEW_SIMPLY2021",  # required(str): login token
    "search_phrase": "hat",                # required(str):
  }
```
其中`search_phrase`的值是用户输入的搜索keyword（string），比如"hat"、"best shoes"等。
- 调用方法：POST
- 参数格式：JSON
- 上述API的返回值为JSON格式的数据，格式如下：

```
{
  product_trends: [
  {
      name: "hat",
      search_msv: [
        { date: "2015-9", sv: 161700 },
        { date: "2015-10", sv: 169950 },
        ......
        { date: "2021-6", sv: 353280 },
        { date: "2015-7", sv: 450000 },
      ],
    },
    ...
  ],
  ...
}
```

其中:
- 完成此题目将会需要用到API返回的JSON中的`product_trends`（对应的是搜索结果里的Related product trends面积图，date对应横轴，sv对应纵轴）；
- 返回的结果中还会包含`product_launch_data`和`products`，请忽略这两项数据。
