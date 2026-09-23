```Mermaid
flowchart TD
    A[LLM 原始文本输出] --> B{是否包含 Thought: 和 Action: ?}
    B -->|是| C[切分提取 Thought 思考内容]
    C --> D[切分提取 Action 工具名称]
    D --> E[提取 Action Input 参数字符串]
    E --> F[json.loads 将参数转为字典]
    F --> G[返回结构化字典包含 thought 和 action]
    B -->|否 或 解析出错| H[走兜底逻辑: 标记 action 为 None, 直接输出 answer]

```




