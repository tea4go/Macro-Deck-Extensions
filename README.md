## Macro Deck 扩展商店
本仓库是 Macro Deck 2 扩展商店的构建清单。

所有要包含到 Macro Deck 中的组件都必须拉取到此仓库中进行构建/打包。

### 如何发布你的内容

### 前提条件
- 你需要为你的扩展准备一个仓库（适用于插件和图标包）
- 你需要选择一个包 ID
  >选择包 ID 时，请确保遵循以下规则：
  >- 不能包含空格
  >- 使用格式：你的名称.你的扩展名称
      
   示例：SuchByte.MacroDeckcolorfulgenericicons
- 你的扩展需要一个 ExtensionManifest.json 文件，其内容应如下所示：
```json
{
   "type" : "Plugin|IconPack",
   "name" : "你的扩展名称", （设定后不可更改）
   "author" : "你的名字",
   "repository" : "https://github.com/you/Your-Repository",
   "packageId" : "你的名称.扩展名称", （不能包含空格和特殊字符，设定后不可更改）
   "version" : "1.0.0", （推荐格式：主版本.次版本.修订号）
   "target-plugin-api-version" : 40, （可在 Macro Deck 设置中找到）
   "target-macro-deck-version" : "1.13.0", （当前用于开发的版本）
   "dll" : "My Plugin.dll" （仅插件需要）
   "author-discord-userid": "9876545678765" （可选：你的 Discord 用户 ID，用于获取支持）
}
```

### 仓库根目录文件结构
#### 插件
```
ExtensionManifest.json
MyPlugin.csproj
ExtensionIcon.png
MyPlugin.cs
.
.
.
```
#### 图标包
```
ExtensionManifest.json
ExtensionIcon.png
MyIcon1.png
SomeotherIcon.png
.
.
.
```

### 规则
#### 通用规则
- 不要直接向此仓库添加文件
  > 请使用工作流自动将扩展添加为子模块
#### 插件规则
- 不允许将 .dll 文件作为依赖项
- 确保你拥有使用所选库的权限
#### 图标包规则
- 确保你拥有使用和发布所添加图标的权限

### 将你的扩展添加到扩展商店
1. Fork 此仓库
2. 在你的 Fork 仓库中，点击 `Actions` 标签页
3. 点击 `Add/Update Extension` 工作流

   > **注意：** 如果在移动端，请先点击 `Select workflow` 按钮
   
4. 点击 `Run workflow` 按钮
5. 填写详细信息，然后点击字段下方绿色的 `Run workflow` 按钮
6. 在你的主分支上，向上游仓库创建一个 PR
  - 这是必须的，因为通过 Actions 的权限比 Web UI 更严格
7. 你的扩展将自动进行校验和构建。之后，管理员将审核你的提交。
