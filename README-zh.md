<div align="center">

# Suna - 开源通用型AI代理

（代表您行动）

![Suna截图](frontend/public/banner.png)

Suna是一个完全开源的AI助手，帮助您轻松完成现实世界的任务。通过自然对话，Suna成为您的数字伙伴，用于研究、数据分析和日常挑战——结合强大的功能和直观的界面，了解您的需求并提供结果。

Suna的强大工具包括无缝的浏览器自动化以导航网络和提取数据、用于文档创建和编辑的文件管理、网络爬取和扩展搜索功能、用于系统任务的命令行执行、网站部署以及与各种API和服务的集成。这些功能协同工作，让Suna能够通过简单的对话解决您的复杂问题并自动化工作流程！

[![许可证](https://img.shields.io/badge/License-Apache--2.0-blue)](./license)
[![Discord关注](https://dcbadge.limes.pink/api/server/Py6pCBUUPw?style=flat)](https://discord.gg/Py6pCBUUPw)
[![Twitter关注](https://img.shields.io/twitter/follow/kortixai)](https://x.com/kortixai)
[![GitHub仓库星标](https://img.shields.io/github/stars/kortix-ai/suna)](https://github.com/kortix-ai/suna)
[![问题](https://img.shields.io/github/issues/kortix-ai/suna
)](https://github.com/kortix-ai/suna/labels/bug)
</div>


## 目录

- [Suna架构](#project-architecture)
  - [后端API](#backend-api)
  - [前端](#frontend)
  - [代理Docker](#agent-docker)
  - [Supabase数据库](#supabase-database)
- [本地运行/自托管](#run-locally--self-hosting)
  - [要求](#requirements)
  - [先决条件](#prerequisites)
  - [安装步骤](#installation-steps)
- [致谢](#acknowledgements)
- [许可证](#license)

## 项目架构

![架构图](docs/images/diagram.png)

Suna由四个主要组件组成：

### 后端API
Python/FastAPI服务，处理REST端点、线程管理以及与Anthropic和其他通过LiteLLM集成的LLM集成。

### 前端
Next.js/React应用程序，提供响应式UI，包括聊天界面、仪表板等。

### 代理Docker
每个代理的隔离执行环境 - 具有浏览器自动化、代码解释器、文件系统访问、工具集成和安全功能。

### Supabase数据库
处理数据持久化，包括认证、用户管理、对话历史、文件存储、代理状态、分析和实时订阅。

## 用例

1. **竞争对手分析** ([观看](https://www.suna.so/share/5ee791ac-e19c-4986-a61c-6d0659d0e5bc)) - *"分析英国医疗行业我的下一家公司的市场。给我主要参与者、他们的市场规模、优势和劣势，并添加他们的网站URL。完成后，生成一份PDF报告。"*

2. **风投清单** ([观看](https://www.suna.so/share/804d20a3-cf1c-4adb-83bb-0e77cc6adeac)) - *"根据管理资产规模给我美国最重要的风险投资基金列表。给我网站URL，如果可能的话，提供一个联系他们的电子邮件。"*

3. **寻找候选人** ([观看](https://www.suna.so/share/3ae581b0-2db8-4c63-b324-3b8d29762e74)) - *"上LinkedIn，找到10个可用的配置文件 - 他们现在没有工作 - 适合初级软件工程师职位，位于德国慕尼黑。他们应该至少有一个计算机科学或任何相关领域的学士学位，以及任何领域/角色的1年经验。"*

4. **公司旅行规划** ([观看](https://www.suna.so/share/725e64a0-f1e2-4bb6-8a1f-703c2833fd72)) - *"为我的公司生成一个路线计划。我们应该去加利福尼亚。我们将有8人。考虑到旅行将持续7天 - 2025年4月21日出发，从出发地（法国巴黎）到我们可以做的活动组成旅行。检查接下来几天的天气预报和温度，并基于此规划我们的活动（户外与室内）。"*

5. **Excel工作** ([观看](https://www.suna.so/share/128f23a4-51cd-42a6-97a0-0b458b32010e)) - *"我的公司要求我建立一个Excel电子表格，包含所有意大利彩票游戏（Lotto，10eLotto和Million Day）的信息。基于此，生成并发送给我一个包含所有基本信息（公开信息）的电子表格。"*

6. **自动化活动演讲者寻找** ([观看](https://www.suna.so/share/7a7592ea-ed44-4c69-bcb5-5f9bb88c188c)) - *"找出20位过去一年在会议上发言的欧洲AI伦理演讲者。抓取会议网站，交叉参考LinkedIn和YouTube，并输出联系信息和演讲摘要。"*

7. **总结和交叉引用科学论文** ([观看](https://www.suna.so/share/c2081b3c-786e-4e7c-9bf4-46e9b23bb662)) - *"研究并比较过去5年讨论酒精对我们身体影响的科学论文。生成一份关于讨论我之前写的主题的最重要科学论文的报告。"*

8. **研究+首次联系草稿** ([观看](https://www.suna.so/share/6b6296a6-8683-49e5-9ad0-a32952d12c44)) - *"在LinkedIn上研究我的潜在客户（B2B）。他们应该在清洁技术行业。找到他们的网站和电子邮件地址。之后，根据公司资料，生成一封个性化的首次联系电子邮件，其中我介绍我的公司，该公司为清洁技术公司提供咨询服务，以最大化他们的利润并减少成本。"*

9. **SEO分析** ([观看](https://www.suna.so/share/43491cb0-cd6c-45f0-880c-66ddc8c4b842)) - *"基于我的网站suna.so，生成SEO报告分析，按关键词集群找出排名靠前的页面，并确定我缺少的主题。"*

10. **生成个人旅行** ([观看](https://www.suna.so/share/37b31907-8349-4f63-b0e5-27ca597ed02a)) - *"生成一个5月1日从曼谷出发的伦敦个人旅行。旅行将持续10天。在伦敦市中心找一个在Google评论上至少有4.5分的住宿。为我找到旅途中有趣的户外活动。生成详细的行程计划。"*

11. **最近获得资金的初创公司** ([观看](https://www.suna.so/share/8b2a897e-985a-4d5e-867b-15239274f764)) - *"访问Crunchbase，Dealroom和TechCrunch，按SaaS金融领域的A轮融资筛选，并构建包含公司数据、创始人和外展销售联系信息的报告。"*

12. **抓取论坛讨论** ([观看](https://www.suna.so/share/7d7a5d93-a20d-48b0-82cc-e9a876e9fd04)) - *"我需要找到罗马最好的美容中心，但我想通过使用讨论这个话题的开放论坛来找到它们。上Google，通过查找位于罗马的美容中心讨论来抓取论坛。然后生成一个包含5个最佳评论的美容中心列表。"*

## 本地运行/自托管

Suna可以在您自己的基础设施上自托管。按照以下步骤设置您自己的实例。

### 要求

您需要以下组件：
- 用于数据库和认证的Supabase项目
- 用于缓存和会话管理的Redis数据库
- 用于安全代理执行的Daytona沙箱
- 用于API后端的Python 3.11
- LLM提供商的API密钥（Anthropic）
- 用于增强搜索功能的Tavily API密钥
- 用于网络抓取功能的Firecrawl API密钥

### 先决条件

1. **Supabase**:
   - 创建一个新的[Supabase项目](https://supabase.com/dashboard/projects)
   - 保存您项目的API URL、匿名密钥和服务角色密钥以备后用
   - 安装[Supabase CLI](https://supabase.com/docs/guides/cli/getting-started)

2. **Redis**: 使用以下选项之一设置Redis实例：
   - [Upstash Redis](https://upstash.com/)（推荐用于云部署）
   - 本地安装：
     - [Mac](https://formulae.brew.sh/formula/redis): `brew install redis`
     - [Linux](https://redis.io/docs/getting-started/installation/install-redis-on-linux/): 按照特定发行版的说明操作
     - [Windows](https://redis.io/docs/getting-started/installation/install-redis-on-windows/): 使用WSL2或Docker
   - Docker Compose（包含在我们的设置中）：
     - 如果您使用我们的Docker Compose设置，Redis已包含并自动配置
     - 不需要额外安装
   - 保存您的Redis连接详情以备后用（如果使用Docker Compose则不需要）

3. **Daytona**:
   - 在[Daytona](https://app.daytona.io/)创建一个账户
   - 从您的账户设置生成API密钥
   - 前往[Images](https://app.daytona.io/dashboard/images)
   - 点击"Add Image"
   - 输入`adamcohenhillel/kortix-suna:0.0.20`作为镜像名称
   - 设置`/usr/bin/supervisord -n -c /etc/supervisor/conf.d/supervisord.conf`作为入口点

4. **LLM API密钥**:
   - 获取[Anthropic](https://www.anthropic.com/)的API密钥
   - 虽然其他提供商应该通过[LiteLLM](https://github.com/BerriAI/litellm)工作，但推荐使用Anthropic – 需要为其他提供商调整提示以输出正确的工具调用XML。

5. **搜索API密钥**（可选）:
   - 对于增强的搜索功能，获取一个[Tavily API密钥](https://tavily.com/)
   - 对于网络抓取功能，获取一个[Firecrawl API密钥](https://firecrawl.dev/)
  

6. **RapidAPI API密钥**（可选）:
   - 要启用LinkedIn等API服务，您需要一个RapidAPI密钥
   - 每个服务需要在您的RapidAPI账户中单独激活：
     1. 在相应文件中找到服务的`base_url`（例如，[`backend/agent/tools/data_providers/LinkedinProvider.py`](backend/agent/tools/data_providers/LinkedinProvider.py)中的`"https://linkedin-data-scraper.p.rapidapi.com"`）
     2. 访问RapidAPI市场中的特定API
     3. 订阅该服务（许多提供有限请求的免费层级）
     4. 订阅后，该服务将通过API服务工具对您的代理可用

### 安装步骤

1. **克隆仓库**:
```bash
git clone https://github.com/kortix-ai/suna.git
cd suna
```

2. **配置后端环境**:
```bash
cd backend
cp .env.example .env  # 如果有示例则从示例创建，或使用以下模板
```

编辑`.env`文件并填入您的凭据：
```bash
NEXT_PUBLIC_URL="http://localhost:3000"

# 步骤1中的Supabase凭据
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# 步骤2中的Redis凭据
REDIS_HOST=your_redis_host
REDIS_PORT=6379
REDIS_PASSWORD=your_redis_password
REDIS_SSL=True  # 对于没有SSL的本地Redis设置为False

# 步骤3中的Daytona凭据
DAYTONA_API_KEY=your_daytona_api_key
DAYTONA_SERVER_URL="https://app.daytona.io/api"
DAYTONA_TARGET="us"

# Anthropic
ANTHROPIC_API_KEY=

# OpenAI API:
OPENAI_API_KEY=your_openai_api_key

# 可选但推荐
TAVILY_API_KEY=your_tavily_api_key  # 用于增强搜索功能
FIRECRAWL_API_KEY=your_firecrawl_api_key  # 用于网络抓取功能
RAPID_API_KEY=
```

3. **设置Supabase数据库**:
```bash
# 登录Supabase CLI
supabase login

# 链接到您的项目（在Supabase仪表板中找到您的项目参考）
supabase link --project-ref your_project_reference_id

# 推送数据库迁移
supabase db push
```

然后，再次访问Supabase网络平台 -> 选择您的项目 -> 项目设置 -> 数据API -> 在"公开架构"中添加"basejump"（如果尚未添加）

4. **配置前端环境**:
```bash
cd ../frontend
cp .env.example .env.local  # 如果有示例则从示例创建，或使用以下模板
```

   编辑`.env.local`文件：
```
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
NEXT_PUBLIC_BACKEND_URL="http://localhost:8000/api"  # 用于本地开发
NEXT_PUBLIC_URL="http://localhost:3000"
```

   注意：如果您使用Docker Compose，请使用容器名称而不是localhost：
```
NEXT_PUBLIC_BACKEND_URL="http://backend:8000/api"  # 使用Docker Compose运行时使用此项
```

5. **安装依赖**:
```bash
# 安装前端依赖
cd frontend
npm install

# 安装后端依赖
cd ../backend
pip install -r requirements.txt
```

6. **启动应用程序**:

   在一个终端中，启动前端：
```bash
cd frontend
npm run dev
```

   在另一个终端中，启动后端：
```bash
cd backend
python api.py
```

5-6. **Docker Compose替代方案**:

在使用Docker Compose运行之前，确保您的环境文件正确配置：
- 在`backend/.env`中，按上述说明设置所有必需的环境变量
  - 对于Redis配置，使用`REDIS_HOST=redis`而不是localhost
  - Docker Compose设置将自动设置这些Redis环境变量：
    ```
    REDIS_HOST=redis
    REDIS_PORT=6379
    REDIS_PASSWORD=
    REDIS_SSL=False
    ```
- 在`frontend/.env.local`中，确保设置`NEXT_PUBLIC_BACKEND_URL="http://backend:8000/api"`以使用容器名称

然后运行：
```bash
export GITHUB_REPOSITORY="your-github-username/repo-name"
docker compose -f docker-compose.ghcr.yaml up
```

如果您要本地构建镜像而不是使用预构建的镜像：
```bash
docker compose up
```

Docker Compose设置包括一个Redis服务，后端将自动使用它。


7. **访问Suna**:
   - 打开您的浏览器并导航到`http://localhost:3000`
   - 使用Supabase认证注册一个账户
   - 开始使用您的自托管Suna实例！

## 致谢

### 主要贡献者
- [Adam Cohen Hillel](https://x.com/adamcohenhillel)
- [Dat-lequoc](https://x.com/datlqqq)
- [Marko Kraemer](https://twitter.com/markokraemer)

### 技术
- [Daytona](https://daytona.io/) - 安全代理执行环境
- [Supabase](https://supabase.com/) -
- [Playwright](https://playwright.dev/) - 浏览器自动化
- [OpenAI](https://openai.com/) - LLM提供商
- [Anthropic](https://www.anthropic.com/) - LLM提供商
- [Tavily](https://tavily.com/) - 搜索功能
- [Firecrawl](https://firecrawl.dev/) - 网络抓取功能
- [RapidAPI](https://rapidapi.com/) - API服务


## 许可证

Kortix Suna根据Apache许可证2.0版授权。查看[LICENSE](./LICENSE)获取完整许可文本。 