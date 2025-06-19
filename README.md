# Carbon-account
## 碳账户自动积分脚本，本脚本开源的目的是，你可以自己接收Token失效的通知，自助通过Github站点更新你自己的Token，从而快速完成替换，不需要每次都等通知和进行修改。

# 碳账户配置提交工具文档

## 项目概述
此工具用于将您的碳账户配置安全地提交到GitHub仓库（[Carbon-account](https://github.com/jjbb013/Carbon-account)），使您能够集中管理应用凭证和通知设置。

## 使用方法

### 1. 获取GitHub Token
1. 请联系 Will Pan 来获取Github Token，有这个Token才能够向数据库提交你的碳账户Token。

### 2. 填写配置表单
在网页中填写以下字段：

| 字段 | 必填 | 说明 |
|------|------|------|
| **GitHub Token** | 是 | 粘贴您获取的GitHub Token |
| **用户名** | 是 | 应用唯一标识（字母数字组合，不含空格） |
| **应用Token** | 是 | 应用定时任务所需的凭证 |
| **Bark通知URL** | 否 | 通知服务URL（格式：`https://api.day.app/xxxxxx`），当你的碳账户Token失效后，你会收到通知，请到此网站来进行更新。 |

### 3. 提交配置
点击"提交配置"按钮，等待处理完成（页面将显示成功或错误提示）

## Bark通知设置指南
### 1. 下载Bark应用
仅支持iOS设备：
- 访问 [App Store链接](https://apps.apple.com/cn/app/bark-%E7%A7%81%E4%BA%BA%E9%80%9A%E7%9F%A5%E5%B7%A5%E5%85%B7/id1403753865)
- 或直接搜索"Bark"安装

### 2. 获取设备URL
1. 打开Bark应用
2. 点击底部菜单栏的【我的】
3. 点击【复制推送链接】按钮
4. URL格式为：`https://api.day.app/xxxxxxxxxxx`

### 3. 使用历史记录功能
- 提交过的Bark URL会自动保存在本地
- 可以从历史记录中快速选择：
  - **复制**：复制URL到剪贴板
  - **使用**：自动填入URL输入框
  - **移除**：从历史记录中删除

## 功能说明
1. **安全提交**：
   - 配置通过GitHub API安全存储
   - GitHub Token和应用Token在提交后自动清除
   - 所有敏感数据以加密形式存储

2. **Bark历史管理**：
   - 自动保存最多5条最近使用的URL
   - 本地存储不上传GitHub
   - 支持一键复用历史记录

3. **配置更新**：
   - 使用相同用户名提交可覆盖现有配置
   - 每次更新都会记录时间戳
   - 保留barkURL历史（如字段留空则维持原值）

## 注意事项
1. **GitHub Token安全**：
   - 仅供配置提交使用
   - 避免分享或在公共场合展示
   - 完成后可在GitHub设置中撤销

2. **用户名要求**：
   - 需保持全局唯一性
   - 建议使用易记标识（不可含空格）
   - 作为配置文件中的主键

3. **错误处理**：
   - 401错误：Token无效或权限不足
   - 404错误：配置文件首次创建，建议重试提交
   - 表单验证失败：请检查必填字段

4. **数据存储**：
   - 配置存储于：`user-configs.json`
   - 格式：
     ```json
     {
       "username": {
         "appToken": "your_app_token",
         "barkUrl": "https://api.day.app/xxxxxx",
         "updatedAt": "2023-11-15T12:00:00Z"
       }
     }
     ```

## 支持信息
工具官网：[Carbon-account仓库](https://github.com/jjbb013/Carbon-account)  
使用问题：请提交GitHub Issues  
隐私政策：本工具仅存储您主动提交的数据  

> 此工具免费提供服务，配置数据存储在公开GitHub仓库，请勿提交任何个人敏感信息


