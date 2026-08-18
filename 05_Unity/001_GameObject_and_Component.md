## 1. Unity 基本架構

Unity 採用 **Component-Based Architecture（組件式架構）**。

基本關係：

```
Project
│
├── Scene
│
└── Assets
```

Scene 內包含：

```
Scene

└── GameObject

      └── Component
```

---

# 2. Scene

## 定義

Scene 是 Unity 中的遊戲場景。

可以理解為：

> 一個遊戲畫面或關卡的容器。

例如：

```
Main Menu Scene

Level 1 Scene

Boss Arena Scene
```

Scene 儲存：

- GameObject
- Lighting
- Camera
- Environment
- Gameplay objects

---

# 3. GameObject

## 定義

GameObject 是 Unity 中最基本的物件單位。

它本身沒有具體功能。

新建立的空 GameObject：

```
Player
```

只有：

```
Transform
```

---

GameObject 的功能來自 Component。

例如：

```
Player

├── Transform
├── Mesh Renderer
├── Rigidbody
├── Collider
└── PlayerMovement Script
```

---

# 4. Transform

## 定義

Transform 是每個 GameObject 必定具有的 Component。

負責：

- Position（位置）
- Rotation（旋轉）
- Scale（縮放）

例如：

```
Position

X: 0
Y: 1
Z: 5
```

代表物件在 3D 空間中的位置。

---

## 為什麼 Transform 必須存在？

因為 Unity 必須知道：

- 物件在哪裡
- 朝哪裡
- 大小多少

沒有 Transform：

Unity 無法在世界中定位這個物件。

---

# 5. Component

## 定義

Component 是附加在 GameObject 上的功能模組。

GameObject 本身像是一個空容器。

Component 賦予它能力。

---

常見 Component：

|Component|功能|
|---|---|
|Transform|位置、旋轉、縮放|
|Mesh Filter|儲存模型資料|
|Mesh Renderer|顯示模型|
|Collider|碰撞判定|
|Rigidbody|物理運算|
|Animator|動畫|
|Script|自訂行為|

---

# 6. Parent / Child Hierarchy

Unity 使用階層式結構：

```
Player

├── Body
├── Weapon
└── Camera
```

子物件會繼承父物件 Transform。

---

## Position

父物件移動：

```
Player
 |
 Weapon
```

Weapon 會跟著移動。

---

## Rotation

父物件旋轉：

Weapon 會一起旋轉。

---

## Scale

父物件縮放：

Child 也會受到影響。

---

# 7. Script 也是 Component

Unity 中：

```
GameObject

↓

Component

↓

Script
```

例如：

```
Player

├── Transform
├── Animator
├── Collider
└── PlayerMovement.cs
```

Script 只是另一種 Component。

---

# 8. Prefab

## 定義

Prefab 是可以重複使用的 GameObject 模板。

例如：

```
Enemy Prefab

↓

Enemy 001

Enemy 002

Enemy 003
```

修改 Prefab：

所有使用它的物件可以同步更新。

---

常見用途：

- 敵人
- 武器
- 子彈
- 道具
- 特效

---

# 今日重點

- Scene 是遊戲場景。
- GameObject 是場景中的物件。
- Component 賦予 GameObject 功能。
- Transform 定義物件在世界中的位置。
- Script 是 Component。
- Parent / Child 會影響 Transform。
- Prefab 是可重複使用的物件模板。

---

# Unity 核心心智模型

```
Scene

↓

GameObject

↓

Component

↓

Script
```

Unity 遊戲開發就是：

> 建立 GameObject，組合 Component，讓它們產生行為。