## 1. Unity 核心架構

Unity 的遊戲物件架構：

```
Scene
│
└── GameObject
      │
      ├── Component
      │
      └── Script (Component)
```

Unity 採用 **Component-Based Architecture（組件式架構）**。

一個物件不是由一個巨大類別控制，而是由多個 Component 組合而成。

例如：

```
Player

├── Transform
├── Mesh Renderer
├── Animator
├── Rigidbody
├── Collider
├── PlayerMovement
└── PlayerCombat
```

每個 Component 負責一種功能。

---

# 2. GameObject

## 定義

GameObject 是 Unity Scene 中最基本的物件單位。

它本身沒有具體功能，功能來自掛載的 Component。

例如：

空的 GameObject：

```
Player
```

只有：

```
Transform
```

沒有：

- 外觀
- 移動
- 碰撞
- 行為

需要透過 Component 增加功能。

---

# 3. Component

## 定義

Component 是附加在 GameObject 上的功能模組。

常見 Component：

|Component|功能|
|---|---|
|Transform|位置、旋轉、縮放|
|Mesh Renderer|顯示模型|
|Collider|碰撞範圍|
|Rigidbody|物理模擬|
|Animator|動畫控制|
|Script|自訂邏輯|

Unity 的 Script 本質上也是 Component。

例如：

```
Player

↓

PlayerMovement.cs
```

代表 Player 多了一個「移動能力」。

---

# 4. MonoBehaviour

## 定義

MonoBehaviour 是 Unity 提供的基礎類別。

當 Script 繼承 MonoBehaviour：

```
public class PlayerMovement : MonoBehaviour
{

}
```

Unity 才能管理這個 Script。

例如：

- 掛載到 GameObject
- 自動呼叫生命週期函式
- 使用 Unity API

---

## Unity 控制 Script

一般程式：

```
main()
 |
 ↓
自己控制流程
```

Unity：

```
Unity Engine

↓

呼叫自己的 Script

↓

Awake()
Start()
Update()
```

這叫：

**Inversion of Control（控制反轉）**

意思：

不是 Script 控制 Unity。

而是 Unity 控制 Script。

---

# 5. MonoBehaviour Lifecycle

Unity 常見生命週期：

```
Awake()

↓

OnEnable()

↓

Start()

↓

Update()

↓

LateUpdate()

↓

OnDisable()

↓

OnDestroy()
```

---

# Awake()

## 時機

物件建立後立即執行。

## 用途

初始化自己。

例如：

```
void Awake()
{
    health = 100;
}
```

適合：

- 初始化變數
- 建立自己的資料

---

# OnEnable()

## 時機

Component 被啟用時執行。

例如：

Inspector：

```
PlayerMovement ✓
```

開啟時。

再次啟用也會執行。

用途：

- 開始監聽事件
- 啟動功能

---

# Start()

## 時機

遊戲開始前執行一次。

## 用途

開始使用其他物件。

例如：

```
void Start()
{
    enemy = FindObjectOfType<Enemy>();
}
```

差異：

Awake：

> 我準備好自己。

Start：

> 我要開始跟其他物件合作。

---

# Update()

## 時機

每一幀執行一次。

例如：

60 FPS：

```
Update 約執行 60 次 / 秒
```

用途：

需要持續更新的內容。

例如：

- 玩家輸入
- 移動
- 瞄準
- 攝影機更新

---

# 6. Unity Script 執行流程

遊戲開始：

```
Unity Engine

↓

載入 Scene

↓

建立 GameObject

↓

加入 Component

↓

Awake()

↓

OnEnable()

↓

Start()

↓

每 Frame:

    Update()

↓

遊戲結束

↓

OnDisable()

↓

OnDestroy()
```

---

# 7. 重要觀念

## 不要把所有東西放進一個 Script

錯誤：

```
PlayerController.cs

1000+ lines
```

包含：

- 移動
- 攻擊
- 血量
- 動畫
- 背包
- 技能
- 任務

```

大型專案會難以維護。

---

推薦：
```

Player

├── PlayerMovement  
├── PlayerCombat  
├── PlayerHealth  
├── PlayerInventory  
└── PlayerAnimation

```

每個 Component 負責自己的功能。

---

# 今日重點

- GameObject 是物件容器。
- Component 提供功能。
- Script 是一種 Component。
- MonoBehaviour 讓 Script 能被 Unity 管理。
- Unity 會主動呼叫 Script，而不是 Script 控制 Unity。
- Awake 用於自己初始化。
- Start 用於開始和其他物件互動。
- Update 每幀執行，用於持續更新。
- 大型遊戲應拆分 Component，而不是建立巨大 Script。

---

# Next

Player Movement

將學習：

- Input System
- Vector3
- Transform
- Time.deltaTime
- 基本角色移動
```