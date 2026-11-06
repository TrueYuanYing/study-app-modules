# 验证总览 · 2026-11-06

- [bilingual-live-transcription](https://github.com/TrueYuanYing/bilingual-live-transcription/blob/main/VALIDATION.md)：17项通过；0失败；静态分析无问题；文本CLI示例通过。
- [ai-classroom-assistant](https://github.com/TrueYuanYing/ai-classroom-assistant/blob/main/VALIDATION.md)：47项通过；0失败；静态分析无问题；固定模拟响应示例通过。
- [course-schedule-import](https://github.com/TrueYuanYing/course-schedule-import/blob/main/VALIDATION.md)：90项通过；0失败；合成页面解析示例通过。
- [native-handwriting-notes](https://github.com/TrueYuanYing/native-handwriting-notes/blob/main/VALIDATION.md)：JVM 49项；失败0；错误0；跳过0；独立debug APK构建成功。
- [immersive-focus](https://github.com/TrueYuanYing/immersive-focus/blob/main/VALIDATION.md)：Web 27项、Dart 9项通过；TypeScript检查与Vite构建通过；隔离浏览器开始/暂停/手动恢复/归档/390px无溢出通过。
- [account-quota-service](https://github.com/TrueYuanYing/account-quota-service/blob/main/VALIDATION.md)：94项合成协议/HTTP测试通过；0失败；本机示例health200且支付关闭；Compose YAML解析与两份sh -n通过。

这些是独立核心/模拟测试与构建，不能替代真实支付、邮件、数据库部署或设备长时验证。
