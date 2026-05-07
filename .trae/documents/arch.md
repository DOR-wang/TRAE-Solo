
## 1. Architecture Design
```mermaid
graph TD
    subgraph Frontend
        A[HTML5 Canvas] --> B[Game Engine]
        B --> C[Rendering System]
        B --> D[Input System]
        B --> E[Game Logic]
        E --> F[Mech Controller]
        E --> G[Battle System]
        E --> H[UI Manager]
    end
    subgraph Assets
        I[Pixel Graphics]
        J[Color Palette]
        K[Animation Frames]
    end
    I --&gt; C
    J --&gt; C
    K --&gt; C
    D --&gt; F
    F --&gt; G
    G --&gt; H
```

## 2. Technology Description
- **Frontend**: 纯 HTML5 + JavaScript + CSS3，无需框架
- **渲染技术**: HTML5 Canvas 2D API
- **初始化工具**: 直接创建 HTML 文件，无需构建工具
- **后端**: 无后端，纯前端游戏
- **数据库**: 不需要数据库
- **外部服务**: 不需要外部服务

## 3. Core Code Structure

```
/workspace/
├── index.html          # 主 HTML 文件
└── README.md           # 项目说明文档
```

## 4. Key Classes and Components

### 4.1 Game 类
游戏主控制器，负责：
- 初始化游戏画布
- 管理游戏主循环
- 处理游戏状态（开始、进行中、结束）
- 协调各个子系统

### 4.2 Mech 类
机甲角色类，负责：
- 存储机甲状态（位置、血量、朝向、动作状态）
- 处理机甲移动
- 处理机甲攻击
- 处理机甲防御
- 更新机甲动画帧

### 4.3 Renderer 类
渲染器类，负责：
- 绘制游戏背景
- 绘制机甲角色
- 绘制UI元素（血量条、操作提示等）
- 处理像素风格渲染

### 4.4 InputHandler 类
输入处理类，负责：
- 监听键盘事件
- 管理按键状态
- 将输入映射到游戏操作

### 4.5 BattleSystem 类
战斗系统类，负责：
- 检测攻击碰撞
- 计算伤害
- 管理血量变化
- 判定胜负

## 5. Game Constants

| Constant Name | Value | Description |
|---------------|-------|-------------|
| CANVAS_WIDTH | 960 | 画布宽度（像素） |
| CANVAS_HEIGHT | 540 | 画布高度（像素） |
| GROUND_Y | 450 | 地面Y坐标 |
| MECH_WIDTH | 80 | 机甲宽度 |
| MECH_HEIGHT | 120 | 机甲高度 |
| MAX_HEALTH | 100 | 最大血量 |
| MOVE_SPEED | 5 | 移动速度 |
| ATTACK_DAMAGE | 15 | 攻击伤害 |
| DEFENSE_REDUCTION | 0.7 | 防御减伤比例 |
| ATTACK_COOLDOWN | 500 | 攻击冷却时间（毫秒） |

## 6. Input Mapping

| Player | Action | Key |
|--------|--------|-----|
| Player 1 | Move Left | A |
| Player 1 | Move Right | D |
| Player 1 | Attack | W |
| Player 1 | Defend | S |
| Player 2 | Move Left | ArrowLeft |
| Player 2 | Move Right | ArrowRight |
| Player 2 | Attack | ArrowUp |
| Player 2 | Defend | ArrowDown |
| Both | Restart | R |

## 7. Animation States

| State | Description | Frame Count |
|-------|-------------|-------------|
| IDLE | 待机状态 | 2 |
| WALK | 行走状态 | 4 |
| ATTACK | 攻击状态 | 3 |
| DEFEND | 防御状态 | 2 |
| HIT | 受击状态 | 2 |

## 8. Color Palette

| Color | Hex | Usage |
|-------|-----|-------|
| Background Dark | #0a0a1a | 背景主色 |
| Background Light | #1a1a3a | 背景渐变 |
| Ground | #2a2a4a | 地面颜色 |
| Player1 Primary | #00ffcc | 玩家1主色 |
| Player1 Secondary | #009988 | 玩家1副色 |
| Player2 Primary | #ff3366 | 玩家2主色 |
| Player2 Secondary | #cc2255 | 玩家2副色 |
| Health Bar | #ff4444 | 血量条颜色 |
| Health Bar BG | #333333 | 血量条背景 |
| UI Text | #ffffff | UI文字颜色 |
| UI Border | #888888 | UI边框颜色 |
