# 如何部署一个mkdocs项目
创建一个github项目管理文档  
部署本地开发环境
部署到readthedocs
## 创建一个github项目
登陆github  
创建repositories，默认即可
例如创建
## 部署本地开发环境
把创建好的git项目clone到本地
```git
git clone git@github.com:lewisNFF/PublicTech.git
```
这个时候会生成PublicTech文件夹，里面包含.git文件夹
<br />
初始化mkdocs工程
```
mkdocs new PublicTech
```
这个时候在PublicTech下自动生成mkdocs.yml文件和docs/index.md
<br />
启动工程预览
```
cd PublicTech
mkdocs serve
```
浏览器打开
[http://localhost:8000/](http://localhost:8000/)
就可以看到预览了
<br />
更多的设置请参考mkdocs的[官方使用手册](https://www.mkdocs.org/#getting-started)
<br />
后面的开发流程就和写代码差不多了。
为项目添加md文件，用git管理版本，mkdocs本地预览，readthedocs负责发布  
<br />

## 提交更新到github
添加docs/use_mkdocs.md,内容为本片文档
修改mkdocs.yml
```yml
site_name: My Docs
nav:
    - Home: index.md
    - how_to_use_mkdocs: use_mkdocs.md
theme: readthedocs
```
这个时候在[http://localhost:8000/](http://localhost:8000/)可以看到内容已经添加，如果不行请在命令窗口按一下ctrl+c重新启动mkdocs服务器  
提交到本地git仓库
```git
git add docs/
git add mkdocs.yml
git commit -m "add how to use mkdocs"
```
push到github

```
git push origin master
```
如果遇到没有权限的问题，请自行搜索如何添加ssh key到github
如果一台电脑需要配置两个github账号，需要自行搜索如何设置
## 部署到readthedocs
导入项目，设置仓库地址，文档类型为mkdocs
## 参考项目地址
[https://github.com/lewisNFF/PublicTech.git](https://github.com/lewisNFF/PublicTech.git)
## 其他问题

### 构建失败可能的问题

1. 没有正确的weekhook
没有关联github账号的话，新建项目的地址使用https，不能使用ssh
在管理→集成下添加webhook
2. 出现不识别nav标签的情况。
在docs文件夹下添加requirements.txt[参考](https://github.com/lewisNFF/PublicTech/blob/master/docs/requirements.txt)。旧版本的mkdocs使用pages标签而不是nav
mkdocs==1.0.4

### 设置主题和highlightjs
```yaml
theme:
    name: mkdocs
    highlightjs: true
    hljs_languages:
        - yaml
        - django
```
参考配置文件：
[https://github.com/mkdocs/mkdocs/blob/master/mkdocs.yml](https://github.com/mkdocs/mkdocs/blob/master/mkdocs.yml)