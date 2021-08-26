# 「矩阵未来」后端开发面试题

我们希望你能自觉在5小时完成后端题目任务。结束后给 hr@simplylab.xyz（如果被退回请发送至zt2008@qq.com） 发送题目的解答，邮件主题请用如下的命名规则：投递的简历平台+面试岗位+姓名+电话。

题目的解答提交可以任选以下三种形式中的一种：
* 直接部署后台到您自己的服务器上，将API访问链接发给我们
* 将整个工程文件的压缩包作为邮件附件，请注意提供部署服务器的说明文档
* 注册github账号，把代码上传到github，直接发送github项目链接给我们


在本题目中您可以使用一个轻量级的flask_restful环境，或者您自己熟悉的框架，完成3个非常基本的API

**这是flast_restful的技术文档，请根据需要阅读:**
- [安装参考文档](https://flask-restful.readthedocs.io/en/latest/installation.html)
- [API基本实现的文档](https://flask-restful.readthedocs.io/en/latest/quickstart.html#a-minimal-api)
- [总文档说明](https://flask-restful.readthedocs.io/en/latest/)


**配置好环境后，请实现下面三个最基本的API:**

##### API 1：实现数组的加法功能
* 调用接口： http://127.0.0.1:5000/add
* 调用方法：POST
* 输入参数：JSON格式的需要加法运算的数列，例子如下
```
{
"value_array": [
    { "value":12},
    { "value":18},
    { "value":10}
  ]
}
```
* 输出：为JSON格式的数组，例子如下
```
{"result":40}
```


##### API 2：获得当前的系统日期
* 调用接口： http://127.0.0.1:5000/get_date
* 调用方法：GET
* 输入参数：无
* 输出：为JSON格式的结果Object，例子如下
```
{"date":"2018-04-18"}
```


##### API 3：傻瓜聊天机器人
* 调用接口： http://127.0.0.1:5000/chat
* 调用方法：POST
* 逻辑规则：
  * 输入的句子中含有中文 “您好”，输出回复“您好，您吃了吗？”
  * 输入的句子中含有中文 “再见”，输出回复“回见了您内。”
  * 输入的句子如果同时含有中文 “再见”和“您好”，输出回复“天气不错。”
* 输入参数：JSON格式的输入语句，例子如下
```
{
"msg":"您好吗？"
}
```
* 输出：JSON格式，例子如下
```
{"result":"您好，您吃了吗？"}
```
