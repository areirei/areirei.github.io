# YaKey 0.3.8 下载

旺旺雅思 · 雅基 YaKey 0.3.8

新增英文日记、OpenAI 接入与更紧凑的学习界面。

- 学习空间增加“日记”：按日期浏览、本地搜索、自动保存、手动“保存并批改”。逐项应用、忽略和撤销建议，保留送评原文与历史报告；日记采用独立定性评价，不套用雅思分数。
- 设置页增加 OpenAI 官方 API 接入，使用 Responses API 并显式设置 store:false。支持可编辑模型 ID、模型列表、连接测试与加密配置分享；实际可用模型以账户权限及连接测试为准。已有混元、CloudBase、火山方舟配置不自动切换，视觉模型仍可留空。
- 日记搜索移到左上方，左侧仅显示标题或日期，欢迎说明收纳在 AI 批改旁的“？”提示中，支持悬停、键盘和触摸。
- 日记与雅思批改统一显示动画、已等待时间、真实处理阶段、模型与等待上限；整套批改显示当前 Task 和处理篇数。支持取消与读取失败后恢复，不用虚假百分比或倒计时表示模型进度。
- 修复日记报告生成后读取失败无法恢复的问题；超时或取消后的迟到结果不得覆盖当前内容。模型响应时间仍由平台和模型决定。
- 每日有效交卷、写作修改、题目自查或日记保存计入轻量学习连胜；同日只计一次。学习总览合并陪伴与连胜信息，给练习入口留出空间。
- 正常关闭桌面窗口前保存编辑内容；保存失败时保留窗口。密钥使用操作系统凭据存储，不可用时仅保留在当前进程；日记与学习数据只在本机保存，只有主动点击批改才发送对应内容。

升级保留旧答卷、成绩、录音、笔记、Anki 标识、AI 配置和已下载题包，不自动调用 AI，也不改写历史评分。日记本地使用无需配置 AI。OpenAI 接口兼容测试不等于真实账户联调或雅思评分校准；本版未宣称新的评分准确率。

已安装正式版：在“关于 / 更新”检查更新，下载完成后保存编辑、退出考试或录音，再点击“重启升级”。手动升级请退出旧应用、备份个人数据，并完整替换程序包。

Windows：完整解压 YaKey-Windows-x64.zip，运行 ielts-studio.exe，并保留 yakey-updater.exe。需要 WebView2 Runtime。

Mac：解压 YaKey-macOS-universal.zip，将 YaKey.app 放入可写的应用程序目录。支持 Intel 和 Apple Silicon，最低 macOS 11；当前采用 ad-hoc 签名，未做 Apple 公证。macOS 实机启动、麦克风及升级仍需设备验收，CI 构建不替代实机验证。

首次启动须联网验证签名配置，成功后的使用许可可离线缓存 7 天。试卷按需下载，不随应用打包；73 套文字资料与原页继续兼容，已知缺页及缺音频标注保留。此前 Start-test 启动器使用独立测试数据，不会自动迁入正式目录。

个人数据：Windows 为 %APPDATA%\IELTSStudio；Mac 为 ~/Library/Application Support/IELTSStudio。两个平台 ZIP 均提供 SHA-256 校验文件。源码和程序包不含个人作文、日记、学习记录、API Key 或本机教材。

这里是公共材料下载入口，无需源码仓库访问权限。两个平台的程序包已回下载并按签名目录验证哈希。

| 平台 | 程序包 | 字节数 | SHA-256 |
| --- | --- | ---: | --- |
| darwin | [下载](https://github.com/areirei/areirei.github.io/raw/refs/heads/material/updates/0.3.8/YaKey-macOS-universal.zip) · [校验文件](YaKey-macOS-universal.zip.sha256) | 41711802 | `8c322a135ec322cf8958f3067b16ab99ab4cd20b31f3ce18a8f392846222539d` |
| windows | [下载](https://github.com/areirei/areirei.github.io/raw/refs/heads/material/updates/0.3.8/YaKey-Windows-x64.zip) · [校验文件](YaKey-Windows-x64.zip.sha256) | 20519886 | `22a66bd9f218a171dc469658d4338d73f3e087e9c8b0e532db5510d13b79a806` |
