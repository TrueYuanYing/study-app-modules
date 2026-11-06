# 模块地图与依赖边界

来源路径相对于整合工程；公开仓库中的 `SOURCE-MANIFEST.json` 可逐文件对应。当前基线为 `source/main/outputs/iko-public-beta`，版本0.3.11+94；共享笔记在 `shared/notes`，服务端在 `server/accounts-commerce`。

| 功能/职责 | 产品入口与调用链 | 数据与存储 | 生命周期/资源/权限 | 此次可运行范围与边界 |
| --- | --- | --- | --- | --- |
| 听写 | features/live → LiveSessionController → record/Sherpa worker或系统SpeechRecognizer | 完整ClassSession、PCM单路流、本地课堂记录 | 麦克风/前台服务/通知；停止释放worker与编码器；系统识别自行占麦 | 文本去重/分句/二次结果选择/PCM核心；真模型与麦克风未测 |
| AI智能答题 | QuestionContext → AiAnswerService → 个人API或hostedRequest | 安全存储Key；本地选取最近课堂；云端请求由服务器计量 | CancelToken/总时限；外部Dio由宿主关闭；云接口需网络 | 固定合成响应；协议/流式/上下文/摘要测试；不代表真实模型质量 |
| 课表 | AcademicImportActivity或CoursePageReader → 相同provider/parser/watch → 预览 → CourseStore | 标准课程、明确节次、开学日期；联合保存/回滚/撤销 | WebView用户自行登录；全局CookieManager范围清理；本地MLKit图片权限按需 | DOM/JSON合成采集解析；UI/存储原宿主为reference；校徽与目录数据排除 |
| 笔记 | NotesCoordinator → com.iko.study/notes → NotesWorkspaceHost → 原生InkView | schema3 NoteDocument/AtomicFile；可见访问区间；录音noteOwner | 原生输入不跨Dart；detach清缓存；退出flush；文档/媒体系统选择器 | 28文件原生编辑器+独立Android示例；完整Office/书库资源需额外接入 |
| MADO | StudyHub → StudySceneScreen本地WebView → iko-host → session/world | 宿主快照、会话和小票；恢复先首页手动继续 | Three/TS；DPR/像素预算；退出dispose回执后清WebView/HTTP/音频 | 真实SessionStore/画质/构图核心与无资产页面；生产GLB不分发 |
| SHIO | 原场景haijian入口 → session/opportunity/settings/sound-mix | 取票、休息、有效专注状态与快照 | Three/TS；音频/渲染/触摸监听统一释放 | 会话与声音混合测试；公测入口仍预告 |
| KUMO | Dart focus_flight_screen → FlightClock/GreatCircleRoute及原生音频提醒 | 航班计划/历史；真实时间推导阶段 | Flutter/Dart；退出timer/animation/stopAudio | Dart阶段/路线测试，机场目录降为五测试点；公测入口仍预告 |
| 账号/充值 | account_screen → GoTrue；quota/checkout → account_api → PostgreSQL/ZPAY | 用户会话、订单、额度预占/已用、通知/审计；模型journal | HTTPS/邮件/支付Key仅服务器；回调验签和查单；容量保护 | HTTP/支付mock、迁移SQL与新实例模板；Docker/真实库/SMTP/付款未测 |

## 更新方式

按manifest追溯源文件，重新核对最新CONTEXT/路线/发布记录，比较自有算法与公开适配层，更新SHA和验证结果。不要把此目录反向覆盖产品，不复制任何原Git历史。各仓库reference目录不计入独立示例构建，缺失资源不会被默认为已经验收。
