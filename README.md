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

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_ND_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)

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
