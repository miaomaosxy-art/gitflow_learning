# 成员代码提交流程（标准版）

适用于日常多人协作开发。

---

# 一、完整流程图

```txt
领取任务
   ↓
更新 develop
   ↓
创建 feature 分支
   ↓
本地开发
   ↓
本地自测
   ↓
commit 提交
   ↓
push 到远程
   ↓
创建 PR
   ↓
Code Review
   ↓
修改问题
   ↓
CI 通过
   ↓
合并 develop
   ↓
删除 feature 分支
```

---

# 二、标准操作步骤

## Step 1：先同步最新代码

切换 develop：

```bash
git switch develop
```

拉取最新代码：

```bash
git pull origin develop
```

---

## Step 2：创建自己的功能分支

命名规范：

```txt
feature/功能名
```

例如：

```bash
git switch -c feature/login
```

---

## Step 3：开始开发

开发过程中建议：

- 小步提交
- 一个功能一个 commit
- 经常同步 develop

---

## Step 4：提交前先同步 develop

```bash
git switch develop
git pull origin develop
git switch feature/login
git rebase develop
```

---

## Step 5：解决冲突

```bash
git status
git add .
git rebase --continue
```

---

## Step 6：本地测试

提交前必须：

```txt
√ 编译通过
√ 单元测试通过
√ lint 通过
√ 功能自测通过
```

例如：

```bash
npm run lint
npm run test
npm run build
```

---

## Step 7：Commit 提交

提交规范：

```txt
type(scope): 描述
```

例如：

```bash
git add .
git commit -m "feat(user): 新增短信登录"
```

---

## Step 8：Push 到远程

```bash
git push origin feature/login
```

---

## Step 9：创建 Pull Request（PR）

```txt
feature/login
    →
develop
```

---

# 三、PR 模板

## 标题

```txt
[模块] 功能说明
```

例如：

```txt
[用户模块] 新增短信登录
```

## 描述

```md
## 改动内容
- 新增短信验证码登录
- 增加 JWT 鉴权

## 测试情况
- 本地测试通过
- 联调通过

## 风险
- 无
```

---

# 四、禁止事项

## 禁止直接提交 main

```bash
git push origin main
```

## 禁止强推

```bash
git push -f
```

尤其：

```txt
main
develop
```

---

# 五、推荐团队约定

## commit 要求

```txt
feat:
fix:
refactor:
docs:
```

## PR 要求

```txt
至少 1 人 Review
CI 通过
```

---

# 六、适合贴团队 Wiki 的精简版

```txt
1. 从 develop 拉 feature 分支
2. 开发完成先 rebase develop
3. 本地测试通过
4. commit 规范
5. push 后创建 PR
6. Review 通过才能 merge
7. CI 必须通过
8. 合并后删除分支
9. 禁止直接改 main
10. 禁止强推
```
