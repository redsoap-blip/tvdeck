# tvdeck

为 SteamOS 游戏模式（Steam Machine，16:9 / 4K）、Steam Deck 与大屏幕模式提供 Apple TV / tvOS 风格外观。
适用于 CSS Loader（Decky Loader）的主题。

基于 [**K€YOZ** 的 **tvOS Deck**](https://github.com/zoyekerako/tvos-deck)（MIT 许可）。

[English README](README.md)

## 截图

![主界面：标题位于最近游戏卡片上方](screenshots/home-titles-above.png)
![快捷访问：快速设置面板](screenshots/qam-quick-settings.png)
![游戏详情页](screenshots/game-detail.png)

## 安装

两种方式都需要先安装 [Decky Loader](https://decky.xyz) 以及 **CSS Loader** 插件。

### 用最新 Release（推荐）

1. 从[最新 Release](../../releases/latest) 下载主题压缩包。
2. 解压后把得到的文件夹复制到 `~/homebrew/themes/tvdeck`，最终主题清单应位于 `~/homebrew/themes/tvdeck/theme.json`。
3. 快捷访问（…）→ CSS Loader → 启用 **tvdeck**。
4. 推荐：在 Steam *设置 → 自定义 → 主页 → 大画幅模式（Big Art Mode）* 下使用，以获得 Apple TV 顶栏式主界面。

### 手动安装

1. 把本文件夹复制到 `~/homebrew/themes/tvdeck`。
2. 快捷访问（…）→ CSS Loader → 启用 **tvdeck**。
3. 推荐：在 Steam *设置 → 自定义 → 主页 → 大画幅模式（Big Art Mode）* 下使用，以获得 Apple TV 顶栏式主界面。

文件夹名必须保持 `tvdeck`：CSS Loader 按文件夹名提供主题文件。Release 压缩包解压后本身就是这个文件夹名。

## 选项

| 选项 | 可选值 | 默认值 |
| --- | --- | --- |
| Focus Effect（焦点效果） | Apple TV (Parallax) · Subtle · Off | Apple TV (Parallax) |
| Background（背景） | Graphite · Black (OLED) · Aurora (tvOS 26) | Graphite |
| Footer（底栏） | Steam Default · Minimal · Hidden | Steam Default |
| Keyboard Styling（键盘样式） | Yes · No | Yes |
| Reduce Transparency（减少透明） | Yes · No | No |
| Tabular Numbers（数字等宽对齐） | Yes · No | Yes |
| Colors（配色） | 强调色、开关色 | `#0A84FF` / `#30D158` |
| Hide friends playing（隐藏好友动态） | Yes · No | Yes |
| Recent Games At Bottom（最近游戏置底） | Yes · No | Yes |
| Titles Above Cards（标题上移） | Yes · No | Yes |
| Home Card Lift（卡片浮起） | Yes · No | Yes |
| Play Caret Focus（开始游戏箭头聚焦高亮） | Yes · No | Yes |

## 说明

- `Titles Above Cards` 会把当前聚焦游戏的标签移到最近游戏卡片上方，并隐藏「Recent Games」页头；
  与 `Recent Games At Bottom` 组合时，卡片行固定在底部，标签随之上移。
- Steam 菜单与快捷访问是独立的覆盖窗口，无法模糊其后的游戏画面，因此使用不透明玻璃底色。
- 主题不设置任何字体栈，文字沿用 Steam 自身字体，把字体控制权留给字体插件。
- 非官方粉丝主题，与 Apple、Valve 无关联。

## 致谢

tvdeck 派生自 [**K€YOZ** 的 **tvOS Deck**](https://github.com/zoyekerako/tvos-deck)（上游版本 1.1.0，MIT 许可）。上游版权声明保留在
[LICENSE](LICENSE) 中，修改部分由 Honchane 完成。

隐藏 tab 的做法沿用 [No Home Tabs by Sims](https://deckthemes.com/themes/view?themeId=1f13929d-cb5b-4ab9-985f-a69504e055fe)（v1.0，2023 年）。
本项目还参考了 [Switch Like Home by Sims](https://deckthemes.com/themes/view?themeId=9ac2bf60-66c5-4f50-aa6b-f897465ba328)（v1.4，2024 年）
与 [No Friend Playing Icon by Luna-Terra](https://deckthemes.com/themes/view?themeId=88363437-0fc3-44f7-9ae4-0ced63893aca)（2025 年）。
三者均为第三方 DeckThemes 主题，均非本仓库作者发布。

## Deutsch

Ordner nach `~/homebrew/themes/tvdeck` kopieren, in CSS Loader einschalten und in Steam
*Einstellungen → Anpassung → Startseite → „Große Grafik“* aktivieren.
