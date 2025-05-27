# Poster101K
Poster101K: A Large-scale Dataset for Poster Graphic Layout Generation

Dataset description

...

Download link

...

Tasks illustration

...

implementation details

...

Ablation study

...

Generated layout images

...



# Poster Image Layout Dataset (POSTER101K)

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)

**A large-scale dataset of 101,914 posters with layout annotations**, designed for graphic design analysis, layout generation models, and computer vision research.

![Poster Examples](docs/examples.png)  
*(注：可创建`docs/examples.png`展示带标注的可视化样例)*

## 📥 下载数据集
本仓库不直接存储数据文件。请通过以下方式获取：

### 推荐下载源（Kaggle）：
[![Kaggle](https://img.shields.io/badge/Download_on-Kaggle-20BEFF.svg)](https://www.kaggle.com/yourusername/mpld-100k)

### 备用下载源：
- [Google Drive 压缩包](https://drive.google.com/...)
- [Torrent 磁力链接](magnet:?xt=urn:btih:...) *(推荐批量下载)*

## 🗂️ 数据集结构
```
mpld-100k/
├── posters/               # 海报图片
│   ├── 000001.jpg        # 格式: JPG (RGB, 平均分辨率 2000x3000)
│   └── ...               # 总计 100,000 文件
└── annotations/          # 标注文件
    ├── 000001.json      # JSON格式布局信息
    └── ...               # 与图片一一对应
```

## 📝 标注格式说明
每个JSON文件包含：
```json
{
  "poster_id": "000001",
  "size": {"width": 2000, "height": 3000},
  "regions": [
    {
      "type": "text",
      "bbox": [x1, y1, x2, y2],  // 归一化坐标 (0~1)
      "content": "Movie Title",  // OCR识别文本（可选）
      "font_size": 0.05          // 相对画布高度的比例
    },
    {
      "type": "image",
      "bbox": [x1, y1, x2, y2],
      "object": "face"           // 检测到的主体对象
    }
  ]
}
```

## 🚀 快速开始
### 通过Kaggle API下载：
```bash
pip install kaggle
kaggle datasets download -d yourusername/mpld-100k
unzip mpld-100k.zip
```

### 数据加载示例（Python）：
```python
import json
from PIL import Image

def load_sample(sample_id):
    img = Image.open(f"posters/{sample_id}.jpg")
    with open(f"annotations/{sample_id}.json") as f:
        ann = json.load(f)
    return img, ann
```

## 🤝 参与贡献
欢迎通过以下方式改进数据集：
- 提交Issue报告标注错误
- 通过Pull Request添加新标注字段
- 分享您使用本数据集的研究成果

## 📜 许可协议
本数据集采用 [CC BY 4.0](LICENSE) 许可，使用时需注明来源：
```bibtex
@dataset{mpld-100k,
  author = {Your Name},
  year = {2023},
  title = {Movie Poster Layout Dataset},
  publisher = {Kaggle},
  version = {1.0},
  url = {https://www.kaggle.com/yourusername/mpld-100k}
}
```

---

### **Kaggle数据集描述**  
（填写至Kaggle的数据集描述框）

````markdown
# Movie Poster Layout Dataset (MPLD-100K)

## 数据集概述
包含 **100,000张电影海报** 及其 **布局标注**，适用于：
- 海报设计自动生成（GAN/扩散模型）
- 多模态布局理解（文本+视觉元素关联）
- 平面设计规则挖掘

## 关键特性
✅ **精细标注**：每个海报包含：
- 文本区域（标题、演员表等）的边界框与语义标签
- 视觉元素（人脸、logo等）的位置信息
- 颜色分布统计（主色板提取）

🌍 **多样性**：覆盖1950-2023年多国电影，包含：
- 10种主要语言
- 5种海报尺寸比例
- 多种设计风格（极简主义、插画风等）

## 文件说明
- `posters/`: JPG格式海报，文件名如`[6位ID].jpg`
- `annotations/`: 结构化JSON标注文件

## 使用示例
见Kaggle Notebook示例：[Demo: Poster Layout Analysis](https://www.kaggle.com/yourusername/mpld-demo)

## 伦理声明
- 所有海报均采集自公有领域或遵循合理使用(fair use)原则
- 如您认为某些内容需要移除，请通过Issue联系我们

## 更新日志
- v1.0 (2023-08-20): 初始发布
