# BrisT1D Dataset - `device_data` Processing Notebook  
This repository contains a Jupyter Notebook used to process the `raw_state` device data in the BrisT1D Dataset to the `processed_state` device data.

## Link to BrisT1D Dataset
_The BrisT1D will soon be published on the University of Bristol Data Repository_

## Repository Structure  
```
brist1d_processing/
├── data/
│   ├── raw_state/             # Folder for raw input data
│   └── processed_state/       # Folder for processed output data
├── notebooks/
│   └── raw_to_processed.ipnb  # Jupyter Notebook for processing
├── .gitignore                 # Files to exclude from version control
├── README.md                  # Project documentation
└── requirements.txt           # Required Python dependencies
```

## Features Processed
| Column Name | Data Type  | Unit    | Description |  
|-------------|------------|---------|-------------|  
| `timestamp` | `datetime` | -       | The time and date the reading was taken. For some variables, this corresponds to the end of the interval the data is aggregated over. |  
| `bg`        | `float`    | mmol/L  | Blood glucose level recorded by the continuous glucose monitor. |  
| `insulin`   | `float`    | Units   | Total insulin dose received in the previous five minutes from the insulin pump. |  
| `carbs`     | `float`    | grammes | Carbohydrate intake recorded by the user in the insulin pump or reader. |  
| `hr`        | `integer`  | bpm     | Mean heart rate for the previous five minutes as recorded by the smartwatch. |  
| `dist`      | `float`    | m       | Total distance travelled in the previous five minutes as recorded by the smartwatch. |  
| `steps`     | `integer`  | count   | Total steps taken in the previous five minutes as recorded by the smartwatch. |  
| `cals`      | `float`    | kcal    | Total calories burned in the previous five minutes as recorded by the smartwatch. |  
| `activity`  | `string`   | -       | Labelled activity events, declared by the user. |  
| `device`    | `string`   | -       | Name of the device that was used to collect the data. |  

## Getting Started  

### 1️. Clone the Repository  
```bash
git clone https://github.com/your-username/health-data-processing.git
cd brist1d_processing
```

### 2️. Install Dependencies  
Ensure you have Python installed, then install the required dependencies:  
```bash
pip install -r requirements.txt
```

### 3. Download the BrisT1D Dataset
Download the data and copy the contents of `brist1d_dataset/device_data/raw_state/` to `brist1d_processing/data/raw_state/`.

### 4. Run the Jupyter Notebook  
Launch Jupyter Notebook and open `notebooks/data_processing.ipynb`:  
```bash
jupyter notebook
```
Run each cell to process the raw data.

## Processing Steps (variation across device export platform)
1. **Load raw data** from the `/data/raw_state/` directory. 
2. **Convert timestamps** to a standard format.
3. **Correct for time zones and device misalgnment** where possible.
4. **Clean data** handle missing values, remove duplicates.  
5. **Aggregate data** insulin and activity data to 5-minute intervals.  
6. **Save processed data** in `/data/processed_state/` for analysis.  

## License
This project is licensed under the [Creative Commons Attribution 4.0 International License](LICENSE).
