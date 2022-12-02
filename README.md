# Great Energy Predictor

How much energy will a building consume?

## Dataset - ASHRAE - Great Energy Predictor III

You can download all csv files (2.61 GB) from [kaggle](https://www.kaggle.com/competitions/ashrae-energy-prediction/data).

Initially, this dataset was used for a global competetion. In this competition, participants should develop accurate models of metered building energy usage in the following areas: chilled water, electric, hot water, and steam meters.

Assessing the value of energy efficiency improvements can be challenging as there's no way to truly know how much energy a building would have used without the improvements. The best participants can do is to build counterfactual models. Once a building is overhauled the new (lower) energy consumption is compared against modeled values for the original building to calculate the savings from the retrofit. More accurate models could support better market incentives and enable lower cost financing.

The dataset includes $3$ years of hourly meter readings from over one thousand buildings at several different sites around the world.

### Files

#### train.csv

* `building_id` - Foreign key for the building metadata.

* `meter` - The meter id code. Read as {0: electricity, 1: chilledwater, 2: steam, 3: hotwater}. Not every building has all meter types.

* `timestamp` - When the measurement was taken

* `meter_reading` - The target variable. Energy consumption in kWh (or equivalent). Note that this is real data with measurement error, which we expect will impose a baseline level of modeling error.

#### building_meta.csv

* `site_id` - Foreign key for the weather files.

* `building_id` - Foreign key for training.csv

* `primary_use` - Indicator of the primary category of activities for the building based on [EnergyStar property type definitions](https://www.energystar.gov/buildings/benchmark/understand_metrics/property_types)

* `square_feet` - Gross floor area of the building

* `year_built` - Year building was opened

* `floor_count` - Number of floors of the building

#### weather_[train/test].csv

Weather data from a meteorological station as close as possible to the site.

* `site_id`

* `air_temperature` - Degrees Celsius

* `cloud_coverage` - Portion of the sky covered in clouds, in oktas

* `dew_temperature` - Degrees Celsius

* `precip_depth_1_hr` - Millimeters

* `sea_level_pressure` - Millibar/hectopascals

* `wind_direction` - Compass direction (0-360)

* `wind_speed` - Meters per second

#### test.csv

The submission files use row numbers for ID codes in order to save space on the file uploads. `test.csv` has no feature data; it exists so you can get your predictions into the correct order.

* `row_id` - Row id for your submission file

* `building_id` - Building id code

* `meter` - The meter id code

* `timestamp` - Timestamps for the test data period

#### sample_submission.csv

A valid sample submission.

* All floats in the solution file were truncated to four decimal places; we recommend you do the same to save space on your file upload.
* There are gaps in some of the meter readings for both the train and test sets. Gaps in the test set are not revealed or scored.

# TO DO

#### Maria:

* Preprocessing
* Data Cleaning
* Idea with NaNs replaced by mean

#### Emilija:

* Literature Review
* EDA

#### Claas:

* Idea with dropped NaNs
