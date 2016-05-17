# JPush API Python Client

## 概述
这是 JPush REST API 的 Python 版本封装开发包，是由极光推送官方提供的，一般支持最新的 API 功能。

对应的 REST API 文档：<http://docs.jpush.io/server/rest_api_v3_push/>

## 环境配置

*   pip方式：sudo pip install jpush
*   easy_install方式：sudo easy_install jpush
*   使用源码方式：sudo python setup.py install

## 代码样例

>以下片断来自项目代码里的文件：jpush-api-python-client 中的 examples/push_examples  目录下的 example_all.py
>演示了消息推送，日志设置，异常处理。

```
_jpush = jpush.JPush(app_key, master_secret)
push = _jpush.create_push()
# the default logging level is WARNING,if you set the logging level to "DEBUG",it will show the debug logging.
_jpush.set_logging("DEBUG")
push.audience = jpush.all_
push.notification = jpush.notification(alert="hello python jpush api")
push.platform = jpush.all_
try:
    response=push.send()
except common.Unauthorized:
    raise common.Unauthorized("Unauthorized")
except common.APIConnectionException:
    raise common.APIConnectionException("conn")
except common.JPushFailure:
    print "JPushFailure"
except:
    print "Exception"
```

## 异常说明

+ Unauthorized
    + AppKey，Master Secret 错误，验证失败必须改正。

+ APIConnectionException
    + 包含错误的信息：比如超时，无网络等情况。

+ JPushFailure
    + 请求出错，参考业务返回码。

## HTTP 状态码

参考文档：<http://docs.jpush.io/server/http_status_code/>

Push v3 API 状态码 参考文档：<http://docs.jpush.io/server/rest_api_v3_push/>　

Report API  状态码 参考文档：<http://docs.jpush.io/server/rest_api_v3_report/>

Device API 状态码 参考文档：<http://docs.jpush.io/server/rest_api_v3_device/>

Push Schedule API 状态码 参考文档：<http://docs.jpush.io/server/rest_api_push_schedule/>　

[Release页面](https://github.com/jpush/jpush-api-python-client/releases) 有详细的版本发布记录与下载。