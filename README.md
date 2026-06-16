# ABA 钱包演示应用

这是一个本地化柬埔寨语的手机银行 UI 演示应用，用于展示和测试银行应用的界面交互设计。

## 🎯 功能特性

### 核心功能
- **个人资料管理** - 编辑用户信息、头像、账户详情
- **多账户支持** - 储蓄账户、活期账户、钱包账户切换
- **转账演示** - 支持本地和国际转账流程
- **收据展示** - 交易成功后生成转账收据
- **余额隐藏** - 点击眼睛图标切换余额可见性

### 自定义功能
- **主题配置** - 字体、字号、颜色、圆角半径等
- **布局调整** - 顶部高度、内容偏移、卡片尺寸等
- **文字本地化** - 支持自定义文本和占位符
- **资源替换** - 自定义背景图和图标

## 💾 数据存储

所有配置和用户数据存储在浏览器 localStorage 中：
```javascript
// 存储键
"amba-demo-profile-v2"

// 包含内容
{
  name: "用户名",
  userId: "ID",
  accountNumber: "账户号",
  cardNumber: "卡号",
  balance: "余额",
  currency: "币种",
  receiptName: "收款人名称",
  receiptId: "收据ID",
  receiptSource: "付款来源",
  avatar: "头像数据URL",
  selectedAccount: "当前账户",
  texts: { /* 文本覆盖 */ },
  placeholders: { /* 占位符覆盖 */ },
  assets: { /* 自定义图像 */ },
  theme: { /* 主题配置 */ }
}
```

## 🚀 快速开始

### 1. 基础使用
```bash
# 打开 index.html 在浏览器中
# 或使用本地服务器
python -m http.server 8000
# 访问 http://localhost:8000
```

### 2. 编辑设置
- 点击右上角 **SET** 按钮打开设置面板
- 修改个人信息、账户详情
- 调整主题和布局参数
- 上传自定义图片和图标
- 点击 **រក្សាទុក** (保存) 保存更改

### 3. 测试转账流程
- 点击主屏转账卡片
- 选择转账类型（如 ABA 账户转账）
- 填写收款人账号和转账金额
- 点击转账按钮
- 输入任意密码完成演示

## 📋 屏幕导航

| 屏幕 | 说明 |
|------|------|
| **home** | 主屏幕 - 账户卡片、快速工具、推广卡 |
| **transfer** | 转账选项 - 本地/国际转账方式 |
| **form** | 转账表单 - 填写收款人和金额 |
| **receipt** | 收据页 - 显示交易成功 |

## 🎨 主题变量

在 CSS 中可配置的 CSS 变量（`:root`）：

```css
--text-scale              /* 文字缩放比例 (0.85 - 1.25) */
--hero-position           /* 顶部图位置 */
--home-hero-height        /* 首页顶部高度 px */
--transfer-hero-height    /* 转账页顶部高度 px */
--form-hero-height        /* 表单页顶部高度 px */
--content-offset          /* 内容面板偏移 px */
--panel-radius            /* 主面板圆角 px */
--card-radius             /* 卡片圆角 px */
--account-card-height     /* 账户卡高度 px */
--panel                   /* 主面板背景色 */
--panel-2                 /* 次级面板背景色 */
--custom-font             /* 自定义字体 */
--hero-background         /* 背景图像 URL */
```

## 🖼️ 可自定义的资源

| 资源键 | 说明 |
|--------|------|
| heroBackground | 顶部背景图 |
| topMore | 顶部菜单图标 |
| topBell | 通知图标 |
| topCard | 卡片图标 |
| topSearch | 搜索图标 |
| topCalendar | 日历图标 |
| topBack | 返回按钮 |
| balanceEye | 余额眼睛图标 |
| accountOrnament | 账户卡装饰 |
| toolAccount | 账户工具图标 |
| toolPayment | 付款工具图标 |
| toolCard | 卡片工具图标 |
| toolScan | 二维码工具图标 |
| toolFavorite | 收藏夹工具图标 |
| toolTransfer | 转账工具图标 |
| receive | 收款按钮 |
| send | 汇款按钮 |
| analysis | 分析按钮 |
| heroTransfer | 转账页大图标 |
| ownAccount | 自有账户选项 |
| brandAccount | ABA 账户选项 |
| localBanks | 本地银行选项 |
| cashCode | Cash-by-Code 选项 |
| swiftIcon | SWIFT 国际转账 |
| riaIcon | Ria 国际转账 |
| moneyGramIcon | MoneyGram 国际转账 |
| formLogo | 表单页圆形标志 |

## 🔧 关键函数

### 个人资料管理
```javascript
loadProfile()              // 从 localStorage 加载配置
saveProfile()              // 保存配置到 localStorage
resetProfile()             // 重置为默认值
```

### 数据格式化
```javascript
formatSubmittedAmount()    // 格式化金额 (保留2位小数)
formatLocalDate()          // 格式化日期为柬埔寨语
normalizeMoney()           // 验证和规范化金额
normalizeScale()           // 验证文字缩放 (0.85-1.25)
normalizePixels()          // 验证像素值范围
```

### 界面更新
```javascript
renderProfile()            // 更新所有UI元素
renderTheme()              // 应用主题变量
renderTextOverrides()      // 应用文本覆盖
renderAssetOverrides()     // 应用自定义图像
```

## 🌐 PWA 支持

应用包含 Service Worker 用于离线缓存：
- 自动缓存所有资源
- 网络失败时使用缓存版本
- 支持"添加到主屏幕"

```javascript
// 缓存策略: 缓存优先
缓存 → 网络 → 离线页面
```

## 📱 浏览器兼容性

- ✅ Chrome/Chromium (推荐)
- ✅ Firefox
- ✅ Safari (iOS 13+)
- ✅ Edge

## 🎭 演示模式

这是一个**完全静态的演示应用**，所有交互都是本地的：
- ❌ 无真实交易
- ❌ 无服务器连接
- ❌ 无数据上传
- ✅ 100% 本地存储和处理

**注意**: 用于演示和UI/UX 测试，不应用于生产环境。

## 📝 文本自定义

可在设置面板中自定义的文本和占位符键：

**界面文本** (data-text):
- greeting, defaultAccountLabel, savingsTitle
- receiveAction, sendAction, analysisAction
- toolAccount, toolPayment, toolCard, toolScan, toolFavorite, toolTransfer
- 等更多...

**输入占位符** (data-placeholder):
- recipientPlaceholder, notePlaceholder
- 等更多...

## 🔐 注意事项

⚠️ **这是演示应用，不适合存储真实敏感数据**
- 账户号、卡号等存储在未加密的 localStorage
- 无密码验证机制
- 仅用于 UI/UX 演示

## 📦 文件结构

```
amba-demo/
├── index.html              # 主HTML页面
├── app.js                  # 应用逻辑 (900+ 行)
├── styles.css              # 样式表
├── service-worker.js       # PWA Service Worker
├── manifest.webmanifest    # PWA 清单
├── assets/                 # 静态资源
│   ├── default-avatar.svg
│   ├── khmer-night.svg
│   └── app-icon.png
└── README.md               # 本文件
```

## 🤝 扩展建议

1. **后端集成** - 连接真实的转账API
2. **用户认证** - 添加登录系统
3. **加密存储** - 使用加密 localStorage 库
4. **多语言** - 完整的国际化支持
5. **单元测试** - 数据格式化函数的测试
6. **分析** - 用户交互追踪

## 📄 许可证

演示用途。可自由修改和使用。

---

**最后更新**: 2026年6月16日 | **版本**: 2.0
