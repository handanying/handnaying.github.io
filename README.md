# handnaying.github.io
# 1. js点位符拼接字符串 
[参考](https://blog.csdn.net/qq_23616601/article/details/77481516)
```
String.prototype.format = function () {
            if (arguments.length == 0) return this;
            var param = arguments[0];
            var s = this;
            if (typeof (param) == 'object') {
                for (var key in param)
                    s = s.replace(new RegExp("\\{" + key + "\\}", "g"), param[key]);
                return s;
            } else {
                for (var i = 0; i < arguments.length; i++)
                    s = s.replace(new RegExp("\\{" + i + "\\}", "g"), arguments[i]);
                return s;
            }
        }

使用
var str1 = "hello {0}".format("world"); //log   hello world
var str1 = "我叫{0},性别{1}".format("美男子", "男"); //log 我叫美男子,性别男
var user = {name: "美男子",sex: "男",age: 20};
var str2 = "我叫{name},性别{sex},今年{age}岁".format(user); //我叫美男子,性别男,今年20岁
```
