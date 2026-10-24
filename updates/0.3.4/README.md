# YaKey 0.3.4 下载

本版修复交卷后写作批改的缺失证据校验：题干换行/空白兼容、准确原句还原、明确错误位置与一次修复。评分标准不变，旧成绩、原答卷、修改稿、API配置及73套文字题包保留。升级不自动调用AI；失败的批改请重新点击对应入口，已有报告可选择“重新评分”。

正式客户端可在设置中检查更新，下载完成后保存作文并退出考试/录音，再点击“重启升级”。手动安装请退出旧应用、备份个人数据后完整替换程序包；无需重新导入题库或填写密钥。

Windows完整解压后运行ielts-studio.exe，并保留yakey-updater.exe，需要WebView2。Mac解压后将YaKey.app放入可写应用目录，支持Intel/Apple Silicon，最低macOS 11，目前为ad-hoc签名、未做Apple公证。个人数据位于Windows的%APPDATA%\IELTSStudio，或Mac的~/Library/Application Support/IELTSStudio。

这里是公共材料仓库，无需源码仓库访问权限。源码仓库Release为独立权限入口。应用内更新使用固定公钥验证的签名目录，两个程序包已完整回下载、哈希检查；两平台测试与构建通过，旧版0.3.3更新管理器已验证能发现并下载0.3.4。

| 平台 | 程序包 | 字节数 | SHA-256 |
| --- | --- | ---: | --- |
| darwin | [下载](https://github.com/areirei/areirei.github.io/raw/refs/heads/material/updates/0.3.4/YaKey-macOS-universal.zip) · [校验文件](YaKey-macOS-universal.zip.sha256) | 41589440 | `678d427a5ed82836aac0cae3785c4ae37db7a836be2d0a1b9f2735d5d49f279f` |
| windows | [下载](https://github.com/areirei/areirei.github.io/raw/refs/heads/material/updates/0.3.4/YaKey-Windows-x64.zip) · [校验文件](YaKey-Windows-x64.zip.sha256) | 20455036 | `f7036b993ceec511049adbeab1cad7c0075c77d5767d399ffa4070b82e6179da` |
