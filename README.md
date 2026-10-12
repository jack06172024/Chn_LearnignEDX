# 古文学习AI平台

## 项目简介

古文学习AI平台是国内首个按年龄分层+适配多元学习方式的智能古文学习平台，以AI技术为核心，覆盖古文学习全链路（输入-理解-应用-拓展-社交），提供学习、翻译、内容生成转换、智能助教、社群互动、知识电商等一体化功能。

## 核心特性

### 用户分层
- **少儿组（6-12岁）**：游戏化学习、图文结合、音频伴读
- **中学组（13-18岁）**：考点拆解、错题分析、针对性练习
- **成人组（19岁及以上）**：自主研读、创作交流、社群分享

### 核心功能
1. **AI个性化学习**：基于用户画像生成个性化学习方案
2. **AI古文翻译**：精准翻译，分层解读
3. **AI内容生成**：古文创作、对联配对、文体转换
4. **AI思考助教**：智能答疑、错题分析、思维引导
5. **社群互动**：分层社群、打卡活动、作品分享
6. **知识电商**：数字课程、实物商品、积分兑换

## 技术栈

- **框架**: Next.js 16 (App Router)
- **语言**: TypeScript 5
- **UI组件**: shadcn/ui (基于 Radix UI)
- **样式**: Tailwind CSS 4
- **AI服务**: 豆包大语言模型 (doubao-seed)
- **开发工具**: Coze CLI

## 项目结构

```
src/
├── app/                      # Next.js App Router
│   ├── api/                  # API 路由
│   │   ├── translate/         # 翻译服务
│   │   ├── generate/          # 内容生成服务
│   │   └── qa/               # AI助教问答服务
│   ├── child/                # 少儿组页面
│   ├── teen/                 # 中学组页面
│   ├── adult/                # 成人组页面
│   ├── layout.tsx            # 根布局
│   └── page.tsx             # 通用版首页
├── components/               # React 组件
│   ├── ui/                  # shadcn/ui 组件
│   ├── bottom-nav.tsx        # 底部导航栏
│   ├── top-nav.tsx          # 顶部导航栏
│   └── age-group-selector.tsx # 年龄层选择器
├── lib/                     # 工具函数
│   ├── constants.ts          # 常量配置
│   └── utils.ts             # 通用工具
└── types/                   # TypeScript 类型定义
    └── index.ts             # 全局类型
```

## API 接口

### 翻译服务
**POST** `/api/translate`

请求体：
```json
{
  "text": "床前明月光，疑是地上霜。",
  "ageGroup": "adult"
}
```

响应：
```json
{
  "success": true,
  "data": {
    "originalText": "床前明月光，疑是地上霜。",
    "translatedText": "翻译结果...",
    "annotations": [],
    "reading": ""
  }
}
```

### 内容生成服务
**POST** `/api/generate`

请求体：
```json
{
  "prompt": "请创作一首关于春天的古诗",
  "type": "poem",
  "ageGroup": "adult"
}
```

响应：
```json
{
  "success": true,
  "data": {
    "id": "1768903236267",
    "type": "poem",
    "content": "生成的古诗内容...",
    "prompt": "请创作一首关于春天的古诗",
    "userId": "user-id-placeholder",
    "createdAt": "2026-01-20T10:00:36.267Z"
  }
}
```

### AI助教问答服务
**POST** `/api/qa`

请求体：
```json
{
  "question": "《静夜思》表达了诗人什么样的思想感情？",
  "context": "",
  "ageGroup": "teen"
}
```

响应：
```json
{
  "success": true,
  "data": {
    "id": "1768903251266",
    "question": "《静夜思》表达了诗人什么样的思想感情？",
    "answer": "AI回答内容...",
    "userId": "user-id-placeholder",
    "context": "",
    "timestamp": "2026-01-20T10:00:51.266Z"
  }
}
```

## 开发指南

### 启动开发环境

```bash
# 开发服务已在后台运行（端口 5000）
# 代码修改会自动触发热更新 (HMR)

# 如需重启服务
coze dev 2>&1 > /dev/null &
```

### 构建项目

```bash
# 类型检查
npx tsc --noEmit

# 生产构建
pnpm run build
```

### 运行生产环境

```bash
coze start
```

## 已完成功能

✅ 项目基础架构（类型定义、API路由结构、组件结构）
✅ 通用版首页（未登录游客视图）
✅ 少儿组专属首页（卡通化、游戏化设计）
✅ 中学组专属首页（考点导向、高效学习）
✅ 成人组专属首页（深度赏析、文化拓展）
✅ 底部和顶部导航栏（分层适配）
✅ AI翻译服务（集成豆包大语言模型）
✅ AI内容生成服务（集成豆包大语言模型）
✅ AI助教问答服务（集成豆包大语言模型）

## 待完成功能

⏳ AI翻译与解读模块前端界面
⏳ AI内容生成与转换模块
⏳ 社群互动模块
⏳ 知识电商模块
⏳ 用户画像与分层系统
⏳ 数据库集成
⏳ 对象存储集成

## 部署说明

项目使用 `.coze` 文件配置构建和运行方式，这是项目在沙箱及部署环境中启动的唯一依据。

### 开发环境
```toml
[dev]
build = ["pnpm", "install"]
run = ["pnpm", "dev"]
```

### 部署环境
```toml
[deploy]
build = ["npm", "run", "build"]
run = ["npm", "run", "start"]
```

## 注意事项

1. **AI服务集成**：所有AI功能已集成豆包大语言模型，支持流式输出
2. **年龄层适配**：不同年龄层的内容和界面风格已完全适配
3. **类型安全**：项目使用TypeScript，所有类型定义完整
4. **组件复用**：使用shadcn/ui组件库，保证UI一致性
5. **响应式设计**：支持多终端适配（iOS、Android、Windows、Mac）

## 许可证

MIT License
