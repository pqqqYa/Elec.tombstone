# 0. 说明
1. 和[[liunx指令]]通用
2. 下面的是基于[[vim指令|vim]]来操作的，所以编辑文本用的vim，但git也可以用于vscode等软件
3. git的云端可以用[[github]]，也可以用gitee(国内的)
# 1. 初始化本地库
git init
红色，文件就是存在，但没被追踪
绿色，当前git知道了追踪到了这个文件
# 2. 查看状态
git status
# 3. 追加到暂存区
git add *file* 
![[Pasted image 20221219214437.png]]
修改完了以后需要再次加入到缓存区
# 4. 从暂存区删除
git  rm --cached *file*     
只是暂存区没了而已，不是文件没了
# 5. 将暂存区文件提交到本地库
git commit -m"日志信息" *file*
![[Pasted image 20221219214517.png]]
这个就是版本号
![[Pasted image 20221219214526.png]]
提交了以后，没有东西需要再次提交
![[Pasted image 20221219214536.png]]
修改后，提交新的日志信息，然后提交到本地库
# 6. 查看日志
git reflog
git log    (详细日志，看到谁上传的，完整版本号是啥）
![[Pasted image 20221219214617.png]]
# 7. 版本穿梭
git reset --hard 版本号
![[Pasted image 20221219214634.png]]
# 8. 分支branch
开发自己的分支的时候不会影响主线分支的运行
可以简单理解成”副本“，其实是指针的引用（HEAD->)
![[Pasted image 20221219214702.png]]
## 1. 创建分支
git branch 分支名
## 2. 查看分支
git branch -v
![[Pasted image 20221219214729.png]]
创建新的分支，查看分支
## 3. 切换分支
git checkout 分支名
![[Pasted image 20221219214752.png]]
切换了以后，后面表示分支的字母（蓝色，绿色）会改变
## 4. 合并分支
把指定分支合并到到当前分支上
git merge 分支名
### 1.正常合并
hot-fix有修改但master分支没有改
![[Pasted image 20221219214819.png]]
### 2.冲突合并
hot-fix和master分支都有修改
![[Pasted image 20221219214901.png]]
进入这个状态，正在合并中（看后面的名字（master|MERGING)
![[Pasted image 20221219214927.png]]
HEAD是当前分支的代码
= = = = = =下面的是另外一个分支的代码
直接删除保存就行了，代码行数不要变
![[Pasted image 20221219215030.png]]
合并完了之后提交本地库commit不带文件名，这是看后面就成了（master)说明合并完了
只会修改合并的，不会修改合并过来的
改了master，不改hot-fix