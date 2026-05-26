# GitHub 多人协作规范（团队版）

适用于：3～30 人的软件开发团队  
目标：减少冲突、提高代码质量、规范发布流程

---

# 1. 仓库基础规范

## 1.1 仓库命名

统一使用：

```txt
业务名-项目名
```

例如：

```txt
mall-admin
mall-api
mall-app
```

避免：

```txt
test
new-project
demo-final-v2
```

---

## 1.2 默认分支

推荐：

| 分支 | 用途 |
|---|---|
| main | 生产环境稳定代码 |
| develop | 日常开发主分支 |

禁止直接向 `main` 提交代码。

---

# 2. Git 分支规范（核心）

推荐 Git Flow 简化版。

---

## 2.1 分支类型

### 主分支

| 分支 | 说明 |
|---|---|
| main | 可发布版本 |
| develop | 开发集成分支 |

### 功能分支

格式：

```txt
feature/功能名
```

例如：

```txt
feature/login
feature/order-pay
```

用途：

- 新功能开发
- 从 develop 拉出
- 合并回 develop

### 修复分支

格式：

```txt
fix/问题名
```

例如：

```txt
fix/login-bug
fix/payment-timeout
```

### 热修复分支

格式：

```txt
hotfix/问题名
```

例如：

```txt
hotfix/prod-login-error
```

特点：

- 从 main 拉出
- 修复后同时合并 main + develop

---

# 3. 提交（Commit）规范

必须统一。

推荐使用 Conventional Commits。

## 3.1 提交格式

```txt
type(scope): 描述
```

例如：

```txt
feat(user): 新增用户登录
fix(order): 修复支付超时
docs(readme): 更新部署文档
refactor(auth): 重构权限模块
```

## 3.2 常用 type

| type | 含义 |
|---|---|
| feat | 新功能 |
| fix | Bug 修复 |
| docs | 文档 |
| style | 格式调整 |
| refactor | 重构 |
| test | 测试 |
| chore | 构建/工具 |

## 3.3 禁止

禁止：

```txt
update
修改
111
final
test
```

---

# 4. Pull Request（PR）规范

多人协作最重要的部分。

## 4.1 提交流程

标准流程：

```txt
develop
   ↓
feature/login
   ↓ 开发
push
   ↓
Pull Request
   ↓
Code Review
   ↓
Squash Merge
   ↓
develop
```

## 4.2 PR 标题规范

格式：

```txt
[模块] 功能说明
```

例如：

```txt
[用户模块] 新增短信登录
[订单模块] 修复支付回调问题
```

## 4.3 PR 描述模板

```md
## 改动内容
- 新增登录接口
- 增加 JWT 校验

## 影响范围
- 用户模块
- 网关鉴权

## 测试结果
- 本地测试通过
- 接口联调通过

## 风险
- 无
```

---

# 5. 最实用核心规则

```txt
1. 不直接改 main
2. 所有代码必须 PR
3. PR 必须 Review
4. Commit 必须规范
5. 小步提交
6. CI 必须通过
7. 不允许强推
8. 文档同步更新
```
