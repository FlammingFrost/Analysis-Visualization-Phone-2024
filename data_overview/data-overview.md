## Data Overview

### Metadata

- `phone_brand`(str): The brand of the phone. 22 unique values.
- `phone_model`(str): The model of the phone. 472 unique values.
- `store`(str): The store/retailer where the phone was sold.
- `price`(float): The price of the phone.
- `currency`(str): The currency of the price.
- `price_USD`(float): The price of the phone in USD.
- `storage`(int): The storage (disk space) of the phone (in GB).
- `ram`(int): The RAM of the phone (in GB).
- `Launch`(str): The launch date of the phone.
- `Dimentions`(str): The dimentions of the phone. In format: `Length x Width x Height` mm.
- `Weight`(float): The weight of the phone (in grams).
- `Display_Type`(str): The specs of the display. May contains type of display, luminosity, refresh rate, etc.
- `Display_Resolutions`(str): The resolution of the display. In format: `Width x Height` pixels.
- `OS`(str): The operating system of the phone.
- `NFC`(0-1): Whether the phone has NFC or not.
- `USB`(str): The USB type of the phone.
- `BATTERY`(int): The battery capacity of the phone (in mAh).
- `Features_Sensors`(str): List of sensors.
- `Colors`(str): The available colors of the phone. List.
- `Video`(str): The video recording capabilities of the phone.
- `Chipset`(str): The chipset of the phone.
- `CPU`(str): The CPU specs of the phone.
- `GPU`(str): The GPU specs of the phone.
- `Year`(int): The year of the phone model.
- `Foldable`(0-1): Whether the phone is foldable or not.
- `PPI_density`(int): The pixel per inch density of the display.
- `price_range`(str): The price range of the phone.

### Data Processing and Transformation

#### Price information

For some models, the data conatians prices from multiple stores, in different currencies. To make the data more consistent, the price is only retained in USD by keeping columns `price_USD`. Means of the prices from different stores are used to calculate the price in USD.

Note: A model may have different specs (e.g. storage, RAM) for different prices. Different specs are treated as different (sub)models.

After the transformation, the data contains 709 rows.

### Dimensions

For easier analysis, we split the `Dimentions` column into three columns: `Length`, `Width`, and `Height`. The values are in mm. A new column name `display_ratio` is also added to calculate the ratio of the `Height` to the `Width`.

### Display (Screen) Information

This column is broken down into two columns: `Screen_Tech` and `Screen_Refres_Rate`.

- `Screen_Tech`: 3 types in total: `LCD`, `OLED`, and `AMOLED`.
- `Screen_Refres_Rate`: 3 types in total: `60Hz`, `90Hz`, and `120Hz`.

### USB

The `USB` column is broken down into two columns: `USB_Type` and `USB_Version`.

- `USB_Type`: 3 types in total: `Type-C`, and `Lightning`. Plus a small number of `Micro USB`.
- `USB_Version`: 3 types in total: `2.0`, and `3.x`.

### Colors

Only the number of colors choices is retained in the `Colors` column.

### Video

This column indicates the video recording capabilities of the phone. Reflecting the processing power of the phone. It is transformed to a list of all supported video resolutions.

### Chipset

The `Chipset` column is broken down into two columns: `Chipset_Manufacturer` and `Chipset_(nm)`.

- `Chipset_Manufacturer`: The manufacturer of the chipset.
- `Chipset_(nm)`: The nano-meter technology of the chipset. The smaller the number, the more advanced the technology.

### CPU

Only the number of cores is retained in the `CPU` column. Range from 4 to 10 cores.

## Missing Values

During the data processing, some missing values enmerged from null values and incomplete data. The missing values are filled with the following strategies:

- Online search for the specs of the phone model (manually). The handle most of the missing values.
- Fill with the most mode.



