# POSTER101K: A Large-scale Poster Image Dataset for Graphic Layout Generation

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

![License: CC BY-ND 4.0](https://img.shields.io/badge/License-CC_BY--ND_4.0-blue.svg)
![Python 3.6](https://img.shields.io/badge/Python-3.9-blue.svg)
![Format PNG](https://img.shields.io/badge/Format-PNG_JPG_WEBP-blue.svg)
![Images 70000](https://img.shields.io/badge/Images-100,000-blue.svg)

![Poster Examples](./Dataset_Introduction.pdf)  
![Teaser image](./Datsaet Introduction.pdf)

**Poster101K** is a large-scale image dataset of posters, originally created as a benchmark for graphic layout generation models. It includes 101,914 poster images covering six themes and 549,260 bounding boxes annotating nine types of design elements.



## 📥 Download
本仓库不直接存储数据文件。请通过以下方式获取：

### 推荐下载源（Kaggle）：
[![Kaggle](https://img.shields.io/badge/Download_on-Kaggle-20BEFF.svg)](https://www.kaggle.com/yourusername/mpld-100k)

### 备用下载源：
- [Google Drive 压缩包](https://drive.google.com/...)
- [Torrent 磁力链接](magnet:?xt=urn:btih:...) *(推荐批量下载)*

## 🗂️ 数据集结构
```
Poster101K/
├── images/               # 海报图片
│   ├── 000001.jpg        # 格式: JPG (RGB, 平均分辨率 2000x3000)
│   └── ...               # 总计 100,000 文件
└── annotations/          # 标注文件
    ├── 000001.json      # JSON格式布局信息
    └── ...               # 与图片一一对应
```

## 📝 标注格式说明
每个xml文件包含：
```xml
<annotation>
  <filename>Business_1</filename>
  <category>Business</category>
  <size>
    <width>1000</width>
    <height>1779</height>
  </size>
  <palette> //Color palette of the entire poster
    <color rgb_p="14 29 36 0.35" />
    <color rgb_p="221 225 224 0.28" />
    <color rgb_p="170 185 177 0.19" />
    <color rgb_p="134 119 109 0.097" />
    <color rgb_p="19 105 95 0.09" />
  </palette>
  <layout> //Layout information of each design element
    <element label="Logo" polygon_x="59 297 297 59 59" polygon_y="60 60 147 147 60" color_1="205 219 213 0.53" color_2="149 181 173 0.25" color_3="18 97 83 0.22" />
    <element label="Logo" polygon_x="333 595 595 333 333" polygon_y="51 51 159 159 51" color_1="230 233 235 0.64" color_2="182 207 201 0.19" color_3="21 98 85 0.16" />
    <element label="Title" polygon_x="77 420 420 77 77" polygon_y="1044 1044 1209 1209 1044" color_1="9 22 29 0.74" color_2="245 163 174 0.21" color_3="129 94 103 0.044" />
    <element label="Title" polygon_x="68 542 542 68 68" polygon_y="1259 1259 1374 1374 1259" color_1="9 18 25 0.79" color_2="238 240 241 0.14" color_3="119 125 128 0.064" />
    <element label="Subtitle" polygon_x="79 304 304 79 79" polygon_y="1396 1396 1471 1471 1396" color_1="7 14 20 0.77" color_2="240 241 242 0.17" color_3="121 125 128 0.058" />
    <element label="Caption" polygon_x="75 553 553 75 75" polygon_y="1524 1524 1587 1587 1524" color_1="10 16 23 0.61" color_2="242 172 185 0.35" color_3="119 89 99 0.042" />
    <element label="Text" polygon_x="51 253 253 51 51" polygon_y="453 453 498 498 453" color_1="205 219 211 0.46" color_2="153 181 172 0.42" color_3="54 112 98 0.12" />
    <element label="Text" polygon_x="51 158 158 51 51" polygon_y="577 577 771 771 577" color_1="162 190 183 0.58" color_2="197 217 209 0.29" color_3="45 109 95 0.13" />
  </layout>
</annotation>
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
