## 1. Git 是什麼？

Git 是版本控制系統（Version Control System）。

用途：

- 記錄檔案修改歷史
- 保存不同版本
- 回復錯誤修改
- 與 GitHub 同步

---

# 2. Git 基本概念

## Repository（Repo）

Repository 是 Git 管理的專案資料夾。

例如：

```
Knowledge

↓

Git Repository
```

裡面包含：

```
.git
```

資料夾。

---

## Working Directory

目前正在修改的檔案。

例如：

```
README.md
```

修改後：

Git 會偵測差異。

---

## Staging Area

準備提交的區域。

流程：

```
修改

↓

git add

↓

Staging Area

↓

git commit
```

---

## Commit

Commit 是一次版本紀錄。

例如：

```
docs: add Unity notes
```

代表：

建立一個可回復的版本。

---

# 3. Git 工作流程

基本流程：

```
修改檔案

↓

git status

↓

git add .

↓

git commit

↓

git push
```

---

# 4. Commit Message

格式：

```
type: description
```

---

常用：

## docs

文件修改

例：

```
docs: add Unity lifecycle notes
```

---

## feat

新增功能

例：

```
feat: add player movement
```

---

## fix

修正問題

例：

```
fix: solve camera bug
```

---

## refactor

重構

例：

```
refactor: reorganize scripts
```

---

## chore

雜項設定

例：

```
chore: initialize Unity project
```

---

# 5. GitHub

GitHub 是遠端 Repository 平台。

Git：

管理版本

GitHub：

保存與分享 Git Repository。

---

流程：

```
Local Repository

↓

git push

↓

GitHub Repository
```

---

# 6. .gitignore

## 定義

.gitignore 告訴 Git：

哪些檔案不要管理。

例如：

```
Library/
Temp/
Logs/
```

Unity 產生的快取資料不需要上傳。

---

# 7. Git Status

查看目前狀態：

```
git status
```

可以知道：

- 哪些檔案修改
- 哪些檔案待提交
- 是否同步

---

# 今日重點

Git 的核心：

```
Working Directory

↓

Staging Area

↓

Commit

↓

GitHub
```

Git 不會自動上傳所有東西。

只有：

```
git add
+
git commit
+
git push
```

後的內容才會更新到 GitHub。