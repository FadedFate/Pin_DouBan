# 豆瓣影评抓取 - Python

这里是一个使用selenium工具实现豆瓣网络评论抓取的工具，根据课程作业中实现的更改而来，使用selenium以尽量避免豆瓣的反爬取策略。


## Dependencies

使用了selenium库以尽量避免遭到限制，selenium库安装与使用自行解决，需要在环境路径下或者当前目录下有谷歌浏览器的webdriver:

```python
from selenium import webdriver
import time
import pandas as pd
import argparse
```

## Usage
在bash中的当前路径下运行:
```cmd
python pin_douban.py --user username --passwd password
```
其中：
-  user与passwd为**必填项**，需要提供豆瓣的账号与密码。
- type选择为long或者short，告知程序选择豆瓣长评还是短评，***注意豆瓣短评似乎只能看到前一定的页数***。
- start选择从第几页开始爬取。
- pages选择需要爬取的页数。  
- query代表查询电影名字，默认为流浪地球。  

其中部分args参数可参考下面代码：
```pytohn
parser.add_argument('--type', type=str, default='long',help='choose the type of comment (long or short)')
parser.add_argument('--user', type=str, default=None, required  =  True , help='username')
parser.add_argument('--passwd', type=str, default=None, required  =  True , help='password')
parser.add_argument('--start', type=int, default=0, help='start page')
parser.add_argument('--pages', type=int, default=10,help='page number')
parser.add_argument('--query', type=str, default="流浪地球" ,help='film name')
```
## Note
程序中的time.sleep()控制休眠时间，嫌慢可自行修改，同时豆瓣爬取的时候依然可能退出，建议分段爬取后在合并。
