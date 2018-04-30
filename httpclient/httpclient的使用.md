1. 创建httpclient客户端
2. 创建httpget请求，或者httppost请求
3. 创建多个namevaluepair，并保存到一个list中，如果是httpget请求。使用entityutils将list
字符串化，并且和url拼接
如果是httppost请求。将list封装成UrlEncodedFormEntity，并且httppost将其设置作为参数
4. httpclient执行execute得到response
5. 对response进行操作
