# Tea Shoot Dataset

A comprehensive dataset for tea leaf segmentation with accompanying TSDI (Tea Shoot Development Index) and ambient temperature data from different growing seasons.

## Dataset Overview

This dataset contains **478 annotated images** of tea shoots for computer vision applications, specifically designed for segmentation tasks. The dataset includes both training and validation splits along with environmental data collected during the tea growing seasons.

### Dataset Statistics

- **Training Images**: 440
- **Validation Images**: 38
- **Total Classes**: 4 (labeled as '0', '1', '2', '3')
- **Image Format**: JPG (1280x1280 pixels)
- **Annotation Format**: YOLO format

## Directory Structure

```
Tea_shoot_dataset/
├── train/
│   ├── images/          # Training images
│   └── labels/          # Training annotations (YOLO format)
├── valid/
│   ├── images/          # Validation images
│   └── labels/          # Validation annotations (YOLO format)
├── TSDI/
│   ├── AreaResul_PMS*.xlsx    # TSDI measurement results
│   └── WS*_interpolated_T.csv # Weather station temperature data
├── data.yaml            # Dataset configuration file
├── LICENSE             # MIT License
└── README.md           # This file
```

## Data Description

### Image Data

The images capture tea shoots at various growth stages across different seasons in 2024:
- **Temporal Coverage**: March 2024 - July 2024
- **Image Resolution**: 1280x1280 pixels
- **Naming Convention**: `[ID]_[YYYY_MM_DD-HH_MM_SS]_[coordinates]_jpg.rf.[hash].jpg`

### TSDI Data

Tea Shoot Development Index measurements stored in Excel format:
- `AreaResul_PMS001_3_148.xlsx`
- `AreaResul_PMS002_1_148.xlsx` 
- `AreaResul_PMS002_2_148.xlsx`
- `AreaResul_PMS002_3_148.xlsx`
- `AreaResul_PMS003_3_148.xlsx`

### Environmental Data

Ambient temperature data from weather stations with hourly interpolated measurements:
- **WS01**: Weather Station 1 temperature data
- **WS02**: Weather Station 2 temperature data  
- **WS03**: Weather Station 3 temperature data
- **WS04**: Weather Station 4 temperature data

Temperature data format: `Date, Temperature(°C)` with hourly timestamps.

## Usage

### Data Configuration

The dataset follows YOLO format configuration specified in `data.yaml`:

```yaml
train: ../train/images
val: ../valid/images
test: ../test/images

nc: 4
names: ['0', '1', '2', '3']
```

### Loading the Dataset

For YOLO-based training frameworks:
```python
# Example with YOLOv8
from ultralytics import YOLO

model = YOLO('yolov8n-seg.pt')
results = model.train(data='path/to/data.yaml', epochs=100)
```

## Applications

This dataset is suitable for:
- **Semantic Segmentation**: Identifying different parts of tea shoots
- **Instance Segmentation**: Individual tea leaf detection and segmentation  
- **Growth Stage Classification**: Using temporal image data combined with TSDI
- **Environmental Impact Analysis**: Correlating plant development with temperature data
- **Agricultural Monitoring**: Automated tea plantation monitoring systems

## Data Collection

The dataset was collected using controlled photography setups across multiple tea plantations, with corresponding environmental monitoring through strategically placed weather stations. TSDI measurements provide quantitative growth metrics that complement the visual data.

## Citation

If you use this dataset in your research, please cite:

```bibtex
@dataset{tea_shoot_dataset_2024,
  title={IoT-Based Automated Monitoring and Assessment of Tea Shoot Density Using Canopy Imaging},
  author={HC Chen},
  year={2024},
  url={https://github.com/csc926/Tea_shoot_dataset}
}
```

## License

This dataset is released under the MIT License. See [LICENSE](LICENSE) for more details.


## Contact

For questions about this dataset, please open an issue in this repository.
