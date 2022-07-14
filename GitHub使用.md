<!--
 * @Description: 
 * @Author: luoxu
 * @Date: 2022-07-10 21:45:47
 * @LastEditTime: 2022-07-10 22:31:54
 * @LastEditors: luoxu
 * @Reference: 
-->
## 学习教程
[官方教程:https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)
vscode 与git b站教程：
[视频链接](https://www.bilibili.com/video/BV1h7411f7Ew?spm_id_from=333.337.search-card.all.click&vd_source=5e52f88f26ee5bb22e1aa092d48c5a1e
)
b站视频对应博客：
[博客链接1：智伤帝的博客](https://blog.l0v0.com/posts/94ffdbdf.html)
[博客链接1：博客内容还可以学其他的，已收藏](https://blog.l0v0.com/posts/a91a4c58.html)
其他系统教程：
[菜鸟教程链接](https://www.runoob.com/git/git-tutorial.htmlv)
[其他可参考链接1](https://cloud.tencent.com/developer/article/1450659)
[其他可参考链接2](https://cloud.tencent.com/developer/article/1504684)



## 问题记录
20220710
**问题1**：使用vscode自带的提交按钮提交时报错：Error: Bad status code: 500，显示Microsoft VS Code\resources\app\extensions\git\dist\git-editor有问题
**解决办法**：
[官方链接](https://github.com/microsoft/vscode/issues/154449)
应该是vscode版本更新的问题
**具体操作**
vscode中设置-将Git:use editor as commit input勾选取消

## 待学习
版本回退
gitignore文件的编写

## 分支管理
列出分支：
```bash
git branch 
```
创建分支命令：
```bash
git branch (branchname)
```
切换分支命令:
```bash
git checkout (branchname)
```
切换到哪个分支，使用ls命令则列出该分支下的文件

创建新分支并立即切换到该分支下
```bash
git checkout -b (branchname)
```
删除分支命令：
```bash
git branch -d (branchname)
```
分支合并：
```bash
git merge
```

## .git文件夹学习（进阶）
[学习链接](https://developer.aliyun.com/article/716483#slide-13)