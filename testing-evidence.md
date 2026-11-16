# MergeScope 知识库更新验证记录

记录日期：2026-11-16（Asia/Shanghai）。基线：当前本地 v1.5.0 工作区，未据此确认远端、已安装扩展或发布版本。

## 本次更新范围

- 更新 mergescope-knowledge.md，保留 MS-OVERVIEW 至 MS-SOURCES 原有12个编号，新增 MS-RISK、MS-PREVIEW、MS-INDEX-READ，共15章。
- 修订已停用的模块配置、路径风险和AI失败回退规则报告说明；补充当前四部分报告、五种风险显示状态、高风险归档/定位、正文读取与Markdown渲染。
- 构建器读取正文日期及章节数；重新生成 mergescope-knowledge.html 和 knowledge.html。项目 README 加入知识入口。

## 已执行与待核实边界

- 本次执行 npm test：86项通过，0失败，0跳过。覆盖源码中的Node单元/集成测试；不代表86条真实业务验收用例执行。
- 本次执行 node scripts/build-mergescope-knowledge.mjs：生成15章节离线页面；正文长度以构建器实际输出为准。
- 本次执行 npm run check：通过，检查JavaScript语法、Manifest和资源引用，不代表真实浏览器业务流程执行。
- 本次新增离线HTML页面检查：检查日期/章节数、搜索、分类、空态和响应式；结果见下方“本次离线校验结果”。
- 此前本轮开发已执行 scripts/browser-smoke.mjs 与 scripts/high-risk-smoke.mjs：真实Chromium载入隔离扩展，仓库、AI和SMTP均模拟；中低风险标签与归档保留专项已通过。本次仅更新知识文档，不将此前结果表述为本次重新执行完整业务流程。
- 未执行真实Git平台全链路、真实模型效果评估、真实SMTP授权投递/收件箱确认、生产部署或发布验收。不得将源码断言、模拟通过或文档整理写成这些工作已经完成。

## 已知覆盖缺口

- 高风险结构化结果只校验枚举、非空说明、触发条件/后果和完整差异文件引用，不证明业务因果链或资料语义正确。
- 尚未自动验证所有REF/B引用解释、同名需求版本生效关系、已有用例的完整匹配，以及建议修改用例与“已有用例未提供”的一致性。
- 历史已精简并丢失风险等级的摘要无法恢复等级；本地知识快照不会随源文件自动更新。
- 浏览器存储额度、真实接口权限/分页兼容、实际邮件送达与真实模型遵循提示的效果，应在对应真实环境另行验证。

## 复查入口

- npm test
- npm run check
- node scripts/build-mergescope-knowledge.mjs
- npm run test:browser（模拟API的扩展流程）
- npm run test:risk（模拟Git/AI/SMTP的风险与归档流程）
- node scripts/evidence-metrics-smoke.mjs（报告Markdown/卡片/字段兼容与布局）

本次未提交或推送仓库，也未自动重新导入已安装扩展的本地知识快照。


## 本次离线校验结果

- node scripts/check-mergescope-knowledge.mjs：通过。
- 两个HTML均包含15章；15个知识编号唯一，页面日期为2026-11-16，章节数与Markdown一致。
- 正文提到的47个源码/测试/脚本路径均存在。
- 分类筛选、关键词搜索、无结果空态、重置均通过；320、390、768、1440像素宽度未观察到页面横向溢出。
- 页面加载未观察到JavaScript错误或HTTP/HTTPS外部请求。此检查验证离线知识页面，不代表扩展的真实业务流程重新执行。
- 截图：artifacts/knowledge-base-desktop.png；artifacts/knowledge-base-mobile.png（项目根目录下）。
- 维护后先构建HTML，再运行本脚本；可使用MERGESCOPE_CHROMIUM指定本机测试浏览器。
