# Fit 2 视频自述

# FIT 文件视频叠加生成器

该项目是一个 Python 脚本，用于从 .FIT 文件生成视频叠加。FIT 文件通常用于存储骑自行车、跑步或游泳等活动的 GPS 和其他传感器数据。脚本会解析 FIT 文件，提取相关数据，并创建一系列显示活动指标（如距离、时间、速度、功率和心率）的帧。然后将这些帧组合成一个视频文件。

### 功能

- 解析 .FIT 文件，提取活动数据。

- 生成具有自定义分辨率、颜色、大小和字体的覆盖图。

- 输出活动数据，如距离、时间、速度、功率和心率。

- 创建叠加视频文件。

## 前提条件

开始之前，请确保满足以下要求：

- 已安装 Python 3.x

- 安装了以下 Python 软件包

- 用于解析 FIT 文件的 `fitparse

- 用于图像处理的 `Pillow` (PIL fork)

- 用于创建视频文件的 `moviepy

- 用于处理帧数据的 `numpy

您可以使用以下命令安装所需的软件包：

```bash

pip install -r requirements.txt

```

或

或

pip install fitparse Pillow moviepy numpy

```

什么都行。

## 使用方法

1.克隆此版本库或将脚本下载到本地计算机。

2.将您的 .FIT 文件放到与脚本相同的目录下，或用正确的 FIT 文件路径更新脚本中的 `fit_file_path` 变量。

3.在脚本中自定义视频叠加设置，如分辨率、背景颜色、字体颜色和字体大小。

4.运行脚本：

```bash

python fit_video_overlay.py

```

1.该脚本将生成一个名为 `output_overlay.mp4` 的视频文件，并叠加您的活动数据。

## 自定义

要自定义视频叠加，请更改脚本中的以下变量：

- fit_file_path`：FIT 文件的路径。

- 宽度"、"高度"：视频叠加的分辨率。

- `background_color`：覆盖层的背景颜色。

- `font_color`：字体的颜色。

- `font_size`：字体大小。

- `font`：用于叠加文本的字体。

## 投稿

欢迎贡献。如果您有更好的建议，请 fork 复制并创建拉取请求。您也可以直接以 "enhancement"（改进）为标签打开一个问题。

## 许可证

本项目采用 [MIT License](notion://www.notion.so/haozheli/LICENSE) 许可。

## 联系

如果您对本项目有任何疑问或意见，请在 GitHub 软件源上提交问题。

## 鸣谢

本项目的灵感来自于以引人入胜的方式可视化锻炼数据的需求。感谢 `fitparse`、`Pillow`、`moviepy` 和 `numpy` 库的开发者让这一切成为可能。