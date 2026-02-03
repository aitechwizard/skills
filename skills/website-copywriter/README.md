# Website Copywriter Skill

自动生成 SEO 优化的中英双语网站文案的 AI 技能。

## 功能说明

这个 skill 可以帮助你快速生成：

- ✅ **品牌描述** (Branding description) - 简洁的品牌标语
- ✅ **英雄区徽章** (Hero badge) - 吸引眼球的公告或行动号召
- ✅ **英雄区标题** (Hero title) - 强有力的标题
- ✅ **英雄区描述** (Hero description) - 详细的价值主张

所有内容都经过 SEO 优化，并提供中英双语版本。

## 使用方法

### 在 Claude 中使用

1. 确保这个 skill 已经安装到 `~/.claude/skills/` 目录
2. 在对话中，直接告诉 Claude 你的网站主题，例如：
   - "帮我为 AI 图片编辑器生成网站文案"
   - "我要创建一个代码片段分享平台，生成文案"
   - "生成在线协作白板的网站描述"

3. Claude 会自动使用这个 skill 生成专业的 SEO 文案

### 示例输入输出

**输入：** "帮我生成一个 AI 代码审查工具的网站文案"

**输出：**
```typescript
branding: {
  name: 'CodeReview AI',
  logo: '🔍',
  description: 'Intelligent code review powered by AI',
},
hero: {
  badge: {
    en: '⚡ Catch Bugs Before Production',
    cn: '⚡ 在上线前捕获 Bug',
  },
  title: {
    en: 'Review Code at Lightning Speed',
    cn: '闪电般的代码审查',
  },
  description: {
    en: 'Automate code reviews with AI that catches bugs, suggests improvements, and enforces best practices instantly.',
    cn: '用 AI 自动化代码审查，即时捕获 bug、建议改进并执行最佳实践。',
  },
},
```

## 特点

- 🎯 **吸引力优先** - 文案首先注重吸引用户，而非生硬的 SEO
- 🔍 **SEO 优化** - 自然融入关键词，优化搜索引擎排名
- 🌐 **双语支持** - 自动生成地道的中英文版本
- ⚡ **快速生成** - 几秒内完成专业文案
- 🛠️ **工具导向** - 特别适合工具类网站

## 目录结构

```
website-copywriter/
├── SKILL.md                              # Skill 主文件（使用指南）
├── README.md                             # 使用说明
└── references/
    └── seo-copywriting-guide.md          # SEO 文案最佳实践参考
```

## 最佳实践

1. **提供清晰的主题** - 越具体越好，例如 "AI 驱动的代码编辑器" 比 "编辑器" 更好
2. **说明目标受众** - 如果有特定受众（开发者、设计师等），告诉 Claude
3. **提供竞品参考** - 如果有竞争对手或参考网站，可以提供链接
4. **反馈迭代** - 如果生成的文案不满意，要求调整或重新生成

## 适用场景

- ✅ 创建新网站项目
- ✅ 重新设计网站首页
- ✅ A/B 测试不同文案
- ✅ 快速原型验证
- ✅ 多语言网站本地化

## 不适用场景

- ❌ 需要深度行业专业术语的网站
- ❌ 法律/医疗等需要严格合规的内容
- ❌ 长篇内容（博客文章、白皮书等）

## 常见问题

**Q: 生成的中文文案听起来像翻译的怎么办？**
A: 可以要求 Claude 使用更口语化、现代化的中文表达。

**Q: 关键词密度太高/太低怎么办？**
A: 告诉 Claude 调整关键词使用，强调自然度。

**Q: 想要不同风格的文案怎么办？**
A: 告诉 Claude 你想要的风格（专业、有趣、技术性强等）。

## 许可证

MIT License

## 贡献

欢迎提交问题和改进建议！
