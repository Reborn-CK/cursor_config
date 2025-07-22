# 大文件处理说明

## 问题
`extensions.zip` 文件大小为 242MB，超过了 GitHub 的文件大小限制（100MB）。

## 解决方案

### 方案1：使用 Git LFS（推荐）
```bash
# 安装 Git LFS
git lfs install

# 跟踪大文件
git lfs track "*.zip"

# 添加并提交
git add .gitattributes
git add extensions.zip
git commit -m "使用 Git LFS 管理大文件"
git push
```

### 方案2：分卷压缩
将大文件分割成多个小文件：
```bash
# 分割文件（每个 50MB）
split -b 50M extensions.zip extensions_part_

# 添加所有分卷文件
git add extensions_part_*
git commit -m "添加分卷压缩文件"
git push
```

### 方案3：使用外部存储
- 将文件上传到云存储（如 Google Drive、OneDrive）
- 在 README 中提供下载链接
- 添加解压说明

## 当前状态
- `extensions.zip` 已添加到 `.gitignore`
- 文件保留在本地，不会被提交到 Git
- 需要手动处理大文件传输

## 建议
推荐使用 Git LFS 方案，它专门设计用于处理大文件。 