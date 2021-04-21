# Git使用笔记

## ssh使用
### 生成&添加ssh公钥
```bash

ssh-keygen -t rsa -C "example@mail.com"

cat ~/.ssh/id_rsa.pub
将输出的密钥内容复制
找到gitee设置里的ssh公钥，点击添加，复制密钥内容

```

![生成密钥](https://images.gitee.com/uploads/images/2018/0814/170141_5aa5bc98_551147.png)

### 测试ssh连接

```bash
ssh -T git@gitee.com
```

![测试ssh连接](https://images.gitee.com/uploads/images/2018/0814/170837_4c5ef029_551147.png)


## 撤销未push的commit

* 法一
	1. 找到被次commit之前的节点
	```bash
	git log
	会有许多提交记录，提交记录中commit后面就是节点值(前7位字符)
	```
	2. 撤销
	```bash
	git reset 节点值
	```
* 法二
```bash
git reset --soft HEAD^
```
参数
HEAD^指上一个版本(HEAD~1),HEAD~2就是撤回上两个版本

`--mixed` 不删除代码的改动，撤销commit和add操作 (默认参数)
         
`--soft` 同上，但不撤销add
         
`--hard` 删除代码改动，且撤销commit和add(用了这个参数你这次的改动就全没了！慎用！！！)

## git add 忽略某个文件(夹)


