# AI 课程实验

基于 UC Berkeley CS188 Pacman 框架的人工智能实验，涵盖搜索算法与多智能体对抗搜索。

## 项目架构

```
课程实验/
├── search/                  # 实验 1：搜索算法（v1.004，Python 3）
│   ├── search.py            # 核心实现：DFS、BFS、UCS、A*
│   ├── searchAgents.py      # 搜索问题定义（迷宫、角落、食物等）
│   ├── searchTestClasses.py # 搜索专用测试类
│   ├── eightpuzzle.py       # 八数码问题
│   ├── pacman.py            # 游戏入口
│   ├── pacmanAgents.py      # Pacman 默认智能体
│   ├── game.py              # 游戏状态机（GameState、Agent 等）
│   ├── ghostAgents.py       # 幽灵 AI
│   ├── layout.py            # 地图解析器
│   ├── util.py              # 数据结构（Stack / Queue / PriorityQueue）
│   ├── graphicsDisplay.py   # 图形化显示
│   ├── graphicsUtils.py     # 图形工具函数
│   ├── keyboardAgents.py    # 键盘控制智能体
│   ├── grading.py           # 评分工具
│   ├── autograder.py        # 本地评分脚本
│   ├── submission_autograder.py  # 提交评分脚本
│   ├── testClasses.py       # 通用测试类
│   ├── testParser.py        # 测试用例解析器
│   ├── projectParams.py     # 项目参数配置
│   ├── textDisplay.py       # 文本模式显示
│   ├── commands.txt         # 常用运行命令示例
│   ├── layouts/             # 37 个地图文件 (.lay)
│   └── test_cases/          # 自动评分用例（q1~q8）
│
└── multiagent/              # 实验 2：多智能体对抗搜索（v1.004，Python 3）
    ├── multiAgents.py       # 核心实现：Reflex、Minimax、Alpha-Beta、Expectimax
    ├── multiagentTestClasses.py  # 多智能体专用测试类
    ├── pacman.py            # 游戏入口
    ├── pacmanAgents.py      # Pacman 默认智能体
    ├── game.py              # 游戏状态机
    ├── ghostAgents.py       # 幽灵 AI
    ├── layout.py            # 地图解析器
    ├── util.py              # 数据结构
    ├── graphicsDisplay.py   # 图形化显示
    ├── graphicsUtils.py     # 图形工具函数
    ├── keyboardAgents.py    # 键盘控制智能体
    ├── grading.py           # 评分工具
    ├── autograder.py        # 本地评分脚本
    ├── submission_autograder.py  # 提交评分脚本
    ├── testClasses.py       # 通用测试类
    ├── testParser.py        # 测试用例解析器
    ├── projectParams.py     # 项目参数配置
    ├── textDisplay.py       # 文本模式显示
    ├── layouts/             # 11 个地图文件 (.lay)
    └── test_cases/          # 自动评分用例（q1~q5 + extra）
```

## 实验内容

### 实验 1：搜索算法（search/）

在 Pacman 迷宫中实现经典搜索算法：

| 题目 | 算法                | 关键点                                |
| ---- | ------------------- | ------------------------------------- |
| Q1   | DFS（深度优先搜索） | 栈实现，图搜索去重                    |
| Q2   | BFS（广度优先搜索） | 队列实现，节点+子节点双重去重         |
| Q3   | UCS（一致代价搜索） | 优先队列，按路径代价排序              |
| Q4   | A* 搜索             | 优先队列 + 启发函数（曼哈顿距离）     |
| Q5   | CornersProblem      | 自定义状态表示（位置 + 四角访问状态） |
| Q6   | Corners Heuristic   | 角落问题启发函数设计                  |
| Q7   | Food Heuristic      | 食物问题启发函数设计（需满足一致性）  |
| Q8   | Closest Dot Search  | 最近食物的贪心搜索                    |

### 实验 2：多智能体对抗搜索（multiagent/）

在 Pacman 对抗环境中实现博弈算法：

| 题目 | 算法              | 关键点                                               |
| ---- | ----------------- | ---------------------------------------------------- |
| Q1   | Reflex Agent      | 反射型智能体：基于食物距离 + 幽灵距离的评估函数      |
| Q2   | Minimax           | 经典极小极大搜索，Pacman vs 多个幽灵                 |
| Q3   | Alpha-Beta 剪枝   | 在 Minimax 基础上加入 α-β 剪枝加速                 |
| Q4   | Expectimax        | 期望最大化搜索，幽灵按均匀概率随机行动               |
| Q5   | Better Evaluation | 综合评估函数：食物距离、幽灵距离、剩余食物数、胶囊数 |

## 运行方式

```bash
# 进入对应实验目录
cd search/
# 或
cd multiagent/

# 运行游戏
python pacman.py

# 指定地图和智能体
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs

# 运行自动评分
python autograder.py
```

## 数据结构（util.py）

框架提供三种容器，对应不同搜索策略：

- **Stack** → DFS
- **Queue** → BFS
- **PriorityQueue** → UCS / A*
