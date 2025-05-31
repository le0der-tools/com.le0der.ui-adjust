# Le0der UI适配工具包

该存储库包括实用各类UI适配工具，旨在简化跨设备和跨平台开发。

该工具已按 Unity Package Manager（UPM）规范封装，可通过 Git 地址直接集成到 Unity 项目中。

---

## 📦 包信息
**包名**：`com.le0der.ui-adjust`

**最低支持 Unity 版本**：`2020.3` 

**作者**：[Le0der](https://github.com/le0der)

---

## ✨ 功能特色

- ✅ 支持按宽度、高度或最小缩放比例适配
- ✅ 支持任意 UI 元素缩放（基于 `RectTransform`）
- ✅ 自动监听父容器尺寸变化，无需手动更新
- ✅ 无需每帧计算，性能友好
- ✅ 兼容所有 Canvas 模式（Overlay、Camera、World）
- ✅ 无额外依赖，可独立使用

---

## 📥 安装方式

你可以通过以下任一方式将该工具包集成到你的 Unity 项目中：

---
### ✅ 方法 1：使用 Unity 编辑器内的 Package Manager 添加 Git 地址（推荐）

1. 打开 Unity 的菜单：Window > Package Manager

2. 点击左上角的 + 号按钮

3. 选择 Add package from Git URL...

4. 输入：
```arduino
https://github.com/le0der-tools/com.le0der.ui-adjust.git
```
### ✅ 方法 2：使用 Git URL 添加依赖

1. 打开你的 Unity 项目
2. 编辑文件：`Packages/manifest.json`
3. 在 `"dependencies"` 节点中添加如下内容：

```json
"com.le0der.singleton": "https://github.com/le0der-tools/com.le0der.ui-adjust.git"
```

## 🧩 使用方法
1. 添加组件

   将 `UIAdjustByTarget` 添加到任意 UI GameObject 上（如 Image、Panel 等）。

2. 配置参数

   - **parentRect**：适配参考的父级 `RectTransform`，即你希望根据哪个容器的大小来进行缩放。
   - **targetRect**：要被缩放的目标对象的 `RectTransform`（通常就是这个 GameObject 自身）
   - **adjustType**：
     - `Width`：按宽度缩放
     - `Height`：按高度缩放
     - `WidthOrHeight`：选择最小缩放值，保持完整显示

3. 示例场景说明

   ```scss
   Canvas
   ├── SamplePanel				(显示界面根节点)
   │   ├── Background   		(整个界面点击和显示遮挡)
   │   ├── Root 				(界面内容显示父节点)
   |	|	└──	...				(界面具体内容)
   ```

   ​	示例场景中，`UIAdjustByTarget` 挂载在Root子项上，可以更改不同的分辨率查看适配效果，Root节点下的UI内容始终以最大可显示范围显示。

   ​	可以更改不同的适配模式，观察不同分辨率下的缩放效果，实现UI适配。

## ⚠️ 注意事项

   - `targetRect` 和 `parentRect` 必须为有效的 `RectTransform`，否则将报错,zi
   - 本组件依赖 UI 系统的尺寸变化回调，不支持非 UI 组件
