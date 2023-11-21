
# Search Workflow 使用文档

`@alife/cone-gpt-wrapper` 是一个用于执行低代码搜索提示构建和执行的工作流。

## 安装

在使用 `@alife/cone-gpt-wrapper` 之前，确保你已经安装了所需的依赖项：


## 配置
在你的项目中，确保以下环境变量已被正确设置：

OPENAI_API_KEY=<你的OpenAI API密钥>

## 使用方法

import { searchWorkflow } from '@alife/cone-gpt-wrapper';

### 执行搜索
要执行搜索，你需要提供查询字符串和上下文，然后调用 runWorkflow 方法：

```
const query = '你的查询字符串';
const context = '你的搜索上下文';

searchWorkflow.runWorkflow(apiKey, query, context)
  .then(result => {
    console.log(result); // 输出搜索结果
  })
  .catch(error => {
    console.error(error); // 打印出错信息
  });

```

### 方法
runWorkflow
这是执行整个工作流的方法。它会自动地处理工作流节点和边的逻辑。

#### 参数:

apiKey - 你的OpenAI API密钥。
query - 搜索查询字符串。
context - 与查询相关的上下文信息。
engine - 可选。使用的OpenAI引擎，默认为 'davinci'。
maxTokens - 可选。生成的最大令牌数，默认为 150。

#### 返回值:

返回一个 Promise，它在成功时解析为搜索结果。

### buildPrompt
内部方法，用于构建用于搜索的提示。

#### 参数:

query - 搜索查询字符串。
context - 与查询相关的上下文信息。
返回值:

返回构建好的提示字符串。

### executeSearch
内部方法，用于执行搜索。

####  参数:

prompt - 构建好的提示字符串。
apiKey - 你的OpenAI API密钥。
engine - 使用的OpenAI引擎。
maxTokens - 生成的最大令牌数。
返回值:

返回一个 Promise，它在成功时解析为搜索结果。

### 缓存
为了提高效率，searchWorkflow 使用 node-cache 来缓存搜索结果。默认的标准生存时间（stdTTL）是 100 秒，检查周期（checkperiod）是 120 秒。

### 请求限流
searchWorkflow 使用 Bottleneck 来限制对API的请求频率，以避免达到API速率限制。默认设置为每秒最多3个请求。

### 注意事项
请确保不要泄漏你的 OPENAI_API_KEY。
遵守 OpenAI 使用条款和请求限制。
### 支持
如果你在使用 searchWorkflow 时遇到任何问题，可以检查项目的 README.md 或提交一个issue到项目的仓库。



