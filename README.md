# Mechamusume（机娘）
Preset-logic response system for artificial affective terminal — based on causal-chain architecture.
- 基于逻辑因果律的机娘回应系统原型。

## 核心架构（复合路由状态回应系统）

- 技术原型：小行星化学成分航天采集器（天问二号），技术核心：多隔离任务模块的守卫条件状态切换
- 物理地基：完整四维宇宙理论（正反质量湮灭能量、正负能量诞生质量的最小粒子对 → 绝对/相对引力点+真空能量海的宇宙膨胀原理 → 量子态原子能出固定想要组合的量子态待确定性，统一量子力学和相对论 → 逻辑因果律是宇宙底层逻辑，不可超光速 → 物理规律允许的，一切都能被制造出来）
- 真实实验：2026年中科院高能物理所的反Λ重子与普通质子碰撞并湮灭、2026年美国布鲁克海文国家实验室重离子碰撞使真空中产生了超过一百对的质子与反质子
- 逻辑因果律：可观测事实推演，非数学符号验证（爱因斯坦、维拉·罗宾的学术流派）
- 预设逻辑链：预设对话选项 → 复合路由状态机 → 输出预设文本/语音/live2d美术形象回应
- 回应终端：每个游戏角色的对话文本由作者本人撰写或筛选填入，核心回应文本10000条+变体文本100000条
- 预设AI/生成AI：可选择原生预设逻辑链回应系统（人格稳定）或接入外部API进行角色文本拟合输出（可能幻觉）
- 生成AI技术原理：API模型+RAG知识库（预设文本）=算法拟合输出
- 适用场景：开放世界游戏NPC拟真交互、二次元手游主界面看板娘触碰交互、类视觉小说游戏女主日常交互

## 可拆卸模块
- 核心：输入模块、状态管理模块、路由模块、单角色独立文本/美术/语音回应库ID匹配模块、复合输出模块
- 状态：复合记忆模块、好感模块、情绪模块、意图识别模块、时间模块、场景模块、好友识别模块
- 附加：商店模块、换装模块、独立剧情模式模块、日常意外事件模块、棋牌小游戏模式模块、经营模式模块、小地图角色移动模块、唱歌模块、舞蹈模块
- 社交：好友聊天模块、好友限次数借用服装模块、多人对战模式模块、个人机娘社交单次自定义文本/自定义live2d表情动作/AI生成语音模块
- 系统：系统设置模块、界面UI隐藏/显示模块

## 项目架构（unity/godot）
- 主模块（DialogueEngine）
-    ├── 加载并管理所有独立模块
-    ├── 接收玩家输入 → 多次路由最终状态 → 获取回应ID
-    ├── 根据回应ID查询内置文件夹数据库
-    └── 输出：文本 + Live2D表情 + Live2D动作 + 语音
- 内置文件夹数据库（ScriptableObject资产）
-    ├── 文本库：ID → 回应文本
-    ├── 表情库：ID → Live2D表情参数
-    ├── 动作库：ID → Live2D动作指令
-    ├── 语音库：ID → 语音片段
-    ├── 场景美术库：ID → 场景资源（关键输入切换，不进入终端输出）
-    └── UI美术库：ID → UI资源（系统模块内可启用/隐藏）
- 或者
- res://
- ——core/
- ————MainModuleCompositeStateRouter.cs（复合路由状态机/切换当前互动角色）
- ——data/
- ————VariantLibrary.cs（变体文本随机排序功能）
- ————MenuOption.cs（系统菜单栏）
- ————SaveManager.cs（存档/读档/快进/慢进/回放等）
- ————PlayerState.cs（玩家状态）
- ————IntentType.cs（意图识别-input打字输入的话可以加）
- ————CharacterManager.cs（可互动角色状态）
- ————其他模块自己写
- ——Libraries/
- ————AffectionStrings.cs（好感度变量）
- ——————lic const string xx = "xx";（好感度状态）
- ——————public const int xx_LOWER = -100;    public const int xx_UPPER = -81;（好感度范围阈值）
- ——————public int currentAffection = 0;（当前好感度）
- ——————if (currentAffection >= AffectionStrings.xx_LOWER && currentAffection <= AffectionStrings.xx_UPPER)
		return AffectionStrings.xx;（当前好感度数值范围映射状态）
- ——————return AffectionStrings.xx;（默认返回xx好感度状态）
- ——————currentAffection += amount;（好感度数值变化）
- ——————currentAffection = Mathf.Clamp(currentAffection, -100, 100);（好感度数值边界）
- ————FixedMemoryLibrary.cs（常识记忆变量）
- ————ShortTermMemoryLibrary.cs（短期记忆变量）
- ————ImportantMemoryLibrary.cs（重要记忆变量）
- ————LifePathLibrary.cs（生活路径变量）
- ————可加情绪变量，看自己需求
- ——Scenes/
- ——TextLibraries/
- ————character1（角色1）
- ————character2（角色2）
- ——art/
- ——audio/

## 安装/使用指南
- 声明：开源只是为了占坑，避免大厂凭借资源优势申请专利
- 注释：轻资产项目，团队参与自行担责（国gal团队/二游团队文案水平低下原因导致市场不买单）
- 安装：你们可以自己按照需求用GPT等AI付费版写代码（程序员实习生用AI都能写的玩意，你们还要我系统架构师给你们写啊）
- 代码：不好意思，本会长不想掏钱给AI写代码，你们快写出来给本会长抄，本会长等着白嫖呢，这可是航天军工预设AI自主探索实用级系统架构方案

## 当前状态

- 逻辑链已推演完成，工程架构正在搭建。
- 详见抖音号：25048587714（岁久潜龙）
- 合集名称：理工路径
- 简介：AI拟人正确路径判断→物理化学地基→预设AI实例→项目管理战略→逻辑因果律推演方法→完全体AGI→游戏架构层

## License

MIT
