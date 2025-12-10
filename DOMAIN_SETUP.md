# 域名配置和问题排查指南

## 🔍 "Site not found" 问题排查

### 问题 1：GitHub Pages 未启用

**检查步骤：**
1. 访问：https://github.com/xenon-w/FilterGS.github.io/settings/pages
2. 确认 "Source" 已设置为 `main` 分支和 `/ (root)` 文件夹
3. 如果未配置，请先启用 GitHub Pages

**标准 GitHub Pages URL：**
- https://xenon-w.github.io/FilterGS.github.io/

### 问题 2：自定义域名配置错误

如果使用自定义域名，需要正确配置：

#### 步骤 1：在 GitHub 中添加域名

1. 访问：https://github.com/xenon-w/FilterGS.github.io/settings/pages
2. 在 "Custom domain" 部分输入你的域名（如：`example.com` 或 `www.example.com`）
3. 点击 **Save**

#### 步骤 2：创建 CNAME 文件

在仓库根目录创建 `CNAME` 文件，内容为你的域名：

```
example.com
```

或者如果使用 www：

```
www.example.com
```

#### 步骤 3：配置 DNS 记录

在你的域名注册商（如 GoDaddy、Namecheap、阿里云等）添加 DNS 记录：

**选项 A：使用 CNAME 记录（推荐）**
- **类型**：CNAME
- **主机记录**：`@` 或 `www`（取决于你的域名）
- **记录值**：`xenon-w.github.io`
- **TTL**：3600（或默认值）

**选项 B：使用 A 记录**
- **类型**：A
- **主机记录**：`@`
- **记录值**：GitHub Pages 的 IP 地址（需要查询最新 IP）
  - 185.199.108.153
  - 185.199.109.153
  - 185.199.110.153
  - 185.199.111.153

#### 步骤 4：等待 DNS 传播

- DNS 更改通常需要 24-48 小时生效
- 可以使用工具检查：https://dnschecker.org/

### 问题 3：URL 路径错误

**重要：** 你的仓库名是 `FilterGS.github.io`，不是 `xenon-w.github.io`

**正确的访问地址：**
- ✅ https://xenon-w.github.io/FilterGS.github.io/
- ❌ https://xenon-w.github.io/（这个会 404）

**如果使用自定义域名：**
- ✅ https://yourdomain.com/
- ✅ https://www.yourdomain.com/

### 问题 4：部署尚未完成

**检查部署状态：**
1. 访问：https://github.com/xenon-w/FilterGS.github.io/actions
2. 查看 "pages build and deployment" 工作流
3. 确认显示绿色勾号（成功）

**等待时间：**
- 首次部署：1-5 分钟
- 后续更新：1-3 分钟

## 🔧 快速修复步骤

### 如果使用 GitHub 默认域名：

1. **确认 Pages 已启用**
   ```
   访问：https://github.com/xenon-w/FilterGS.github.io/settings/pages
   确认 Source = main, Folder = / (root)
   ```

2. **使用正确的 URL**
   ```
   https://xenon-w.github.io/FilterGS.github.io/
   ```

3. **检查部署状态**
   ```
   访问：https://github.com/xenon-w/FilterGS.github.io/actions
   ```

### 如果使用自定义域名：

1. **检查 CNAME 文件**
   - 确认仓库根目录有 `CNAME` 文件
   - 文件内容只有域名，没有 http:// 或 https://

2. **检查 DNS 配置**
   - 使用 https://dnschecker.org/ 检查 DNS 是否生效
   - 确认 CNAME 或 A 记录正确

3. **检查 GitHub Pages 设置**
   - 确认自定义域名已添加到 Pages 设置中
   - 等待 SSL 证书自动生成（可能需要几分钟）

## 📝 创建 CNAME 文件（如果需要）

如果需要使用自定义域名，我可以帮你创建 CNAME 文件。

请告诉我：
1. 你的域名是什么？
2. 是否使用 www（如 www.example.com）？

## ✅ 验证清单

- [ ] GitHub Pages 已启用（Settings → Pages）
- [ ] Source 设置为 `main` 分支
- [ ] Folder 设置为 `/ (root)`
- [ ] 部署状态显示成功（Actions 标签）
- [ ] 使用正确的 URL 访问
- [ ] 如果使用自定义域名，CNAME 文件存在
- [ ] DNS 记录已正确配置
- [ ] 等待了足够的时间让 DNS 传播

## 🆘 仍然无法访问？

1. **清除浏览器缓存**
   - 按 Ctrl+Shift+Delete 清除缓存
   - 或使用无痕模式访问

2. **检查浏览器控制台**
   - 按 F12 打开开发者工具
   - 查看 Console 和 Network 标签的错误信息

3. **尝试不同的浏览器**
   - 确认不是浏览器特定问题

4. **检查 GitHub 状态**
   - 访问：https://www.githubstatus.com/
   - 确认 GitHub Pages 服务正常

