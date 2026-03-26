# Moodist 应用打包部署指南

## 📦 应用信息
- **应用名称**: Moodist 白噪音
- **版本**: 0.0.3
- **包名**: cloud.lazycat.app.moodist
- **Docker镜像**: ghcr.io/remvze/moodist:latest
- **国际化支持**: 中文(zh-CN)、英文

## 📋 文件清单
```
moodist-lzc-app/
├── lzc-manifest.yml       # 主配置文件 ✓
├── lzc-build.yml          # 构建配置文件 ✓
├── docker-compose.yml     # Docker编排文件 ✓
├── icon.png               # 应用图标 ✓
├── locales/               # 国际化目录 ✓
│   ├── zh-CN/
│   │   └── manifest.yml
│   └── en/
│       └── manifest.yml
└── README.md
```

## 🚀 打包步骤

### 方式一：懒猫微服Web界面在线打包

1. **登录懒猫微服管理后台**
   - 访问您的懒猫微服管理平台
   - 使用管理员账号登录

2. **进入应用开发界面**
   - 找到"应用开发"或"LPK打包"功能
   - 选择"创建新应用"或"导入应用"

3. **上传项目文件**
   - 将整个项目文件夹上传
   - 或通过Git导入（如果支持）

4. **配置打包参数**
   - 确认版本号: 0.0.3
   - 检查镜像配置: ghcr.io/remvze/moodist:latest
   - 验证国际化配置

5. **执行构建**
   - 点击"构建"或"打包"按钮
   - 等待构建完成

6. **下载LPK包**
   - 下载生成的 .lpk 文件
   - 文件名: `cloud.lazycat.app.moodist-0.0.3.lpk`

### 方式二：使用lzc-build命令行工具

如果您安装了 `lzc-build` 工具：

```bash
# 进入项目目录
cd /home/lx/project-lzc-app/moodist-lzc-app

# 执行打包命令
lzc-build build

# 生成的LPK包将在当前目录
ls -lh *.lpk
```

## 📤 部署步骤

1. **上传LPK包到懒猫微服平台**
   - 登录懒猫微服管理后台
   - 进入"应用管理" → "应用安装"
   - 上传打包好的 .lpk 文件

2. **安装应用**
   - 选择安装位置
   - 配置子域名 (默认: moodist)
   - 启动应用

3. **验证部署**
   - 访问应用: `http://moodist.<your-domain>`
   - 检查应用正常运行
   - 测试国际化功能

## 🔧 配置说明

### 应用配置 (lzc-manifest.yml)
- 支持多实例部署
- 无需GPU加速
- 端口: 8080
- 子域名: moodist

### 国际化配置
- 中文 (zh-CN): Moodist 白噪音
- 英文: Moodist White Noise

## ⚙️ 应用升级

如需后续升级：
1. 修改 `lzc-manifest.yml` 中的版本号
2. 更新Docker镜像版本（如需要）
3. 重新打包
4. 在平台中上传新版本进行升级

## 📝 注意事项

- 确保Docker镜像可访问: ghcr.io/remvze/moodist:latest
- 首次部署需要拉取镜像，可能需要等待
- 应用支持多实例，可同时运行多个副本
- 国际化功能会根据用户系统语言自动切换

## 🆘 常见问题

**Q: 打包失败怎么办？**
A: 检查所有必需文件是否存在，特别是 lzc-manifest.yml 和 docker-compose.yml

**Q: 应用无法启动？**
A: 检查Docker镜像是否正确拉取，查看应用日志获取详细错误信息

**Q: 国际化不生效？**
A: 确认 locales 目录结构正确，语言代码格式为 zh-CN 和 en
