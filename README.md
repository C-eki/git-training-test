## 部署

本项目提供一套 bash 脚本，一键完成构建、测试、启动。详见 `scripts/`。

### 首次部署

```bash
./scripts/deploy.sh --dry-run    # 不真跑，先看执行计划
./scripts/deploy.sh               # 正式部署
./scripts/status.sh               # 查看状态
```

### 日常操作

| 场景 | 命令 |
|------|------|
| 部署最新代码 | `./scripts/deploy.sh` |
| 指定 tag 部署 | `./scripts/deploy.sh --image-tag v1.2.3` |
| 不构建直接启 | `./scripts/deploy.sh --skip-build` |
| 跳过冒烟测试 | `./scripts/deploy.sh --skip-tests` |
| 回滚到上一版 | `./scripts/rollback.sh` |
| 看服务状态 | `./scripts/status.sh` |
| 状态（JSON） | `./scripts/status.sh --json` |

### 日志与备份

- 当前日志：`logs/deploy/latest.log`（软链指向最新一次）
- 历史日志：`logs/deploy/deploy-YYYYMMDD-HHMMSS.log`（自动保留最近 10 份）
- 备份记录：`.deploy-backup/last-image.txt`（供 rollback 使用）

### 配置

所有可调参数在 `scripts/config/deploy.conf`。常改的：
- `SERVICE_PORT`：对外端口
- `HEALTHCHECK_TIMEOUT`：健康检查总超时（秒）
- `MIN_DISK_GB`：部署前最少可用磁盘
# Vision Toolkit - 图像处理工具库

简单易用的计算机视觉工具库，实现常见的图像处理算法。

## 功能特性

### 图像滤波
- ✅ 灰度化转换
- ✅ 高斯模糊
- ✅ Sobel边缘检测
- ✅ Canny边缘检测

### 几何变换
- ✅ 图像旋转
- ✅ 图像缩放
- ✅ 图像翻转

## 安装

```bash
# 克隆仓库
git clone https://github.com/yourusername/vision-toolkit.git
cd vision-toolkit

# 安装依赖
pip install -r requirements.txt
```

## 快速开始

```python
import cv2
from src.filters import gaussian_blur, canny_edge_detection
from src.transforms import rotate, resize

# 读取图像
image = cv2.imread('image.jpg')

# 高斯模糊
blurred = gaussian_blur(image, kernel_size=5)

# 边缘检测
edges = canny_edge_detection(image)

# 旋转45度
rotated = rotate(image, 45)

# 缩放到宽度300
resized = resize(image, width=300)
```

## 运行示例

```bash
python examples/demo.py
```

## 运行测试

```bash
pytest tests/ -v
```

## 项目结构

```
vision-toolkit/
├── src/              # 源代码
├── tests/            # 测试
├── examples/         # 示例
└── README.md         # 文档
```

## 作者

- 姓名：[C]
- 姓名简拼：[C]
- 日期：2026-05-07

## 许可证

MIT License
