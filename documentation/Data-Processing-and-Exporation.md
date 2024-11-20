# Documentation: Data Processing and Exploration
> Expected time to complete: Week 2

## Data Cleaning

### Missing Values
Some weights missing, filled with data from online sources.
| Index | Weight filled |
| ----- | ------------- |
| 1042  | 199.0         |
| 1151  | 202.0         |
| 1395  | 186.0         |

### Not phone category: Tablet (removed)
Removed 3 models from Samsung

### Brands with too few models: (removed)
Sony (9), zte (9), nothing (8), tecno (5), infinix (3), tcl (2), htc (1), cubot (1), blackview (1).

### Cleaned dataset
- `./data/cleaned_data.csv`, with 706 rows and 27 columns.

## Data Processing

### Extract info from text
- Extracted `Lenght`, `Width`, `Height` and `Ratio`(Height/Width) from `Dimensions` column.
- Extracted `Screem_Tech` (LCD/OLED/AMOLED) and `Screen_Refresh_Rate` (Hz) from `Display_Type` column.
- Extracted `USB_Type` (Type-C/Lightning/Micro-USB) and `USB_Version` (2.0/3.x) from `USB` column.
- Reduced `Colors` to number of color options available.
- Extracted `Supported_Video_Resolution` from `Video` column.
- Extracted `Chipset_Manufacturer` and `Chipset_(nm)` (nano-meter for the chipset) from `Chipset` column. Ignore sub-models of the chipset.
- Reduced `CPU` to number of cores.

### Standardization
- `Chipset_Manufacturer`: 'Mediatek' -> 'MediaTek'
- `Year` is consistent with the release year oin `Launch` column. Drop `Year` column.

## Exploratory Data Analysis (EDA)

Detailed in [EDA notebook](../EDA-and-Transformation/eda-transformation.ipynb).

## Data Transformation

Detailed in [EDA notebook](../EDA-and-Transformation/eda-transformation.ipynb).