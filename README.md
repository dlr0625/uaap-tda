# Using Topology to Extract Insights from UAAP Basketball Data
**Authors: Benjamin ANG, Alexander PINO, Dane ROSARIO**

# Project Description
This project explores the application of Topological Data Analysis (TDA) 
to identify groupings among players in the 84th season of the UAAP 
basketball tournament. We leverage the power of giotto-tda, a Python 
library specifically designed for TDA tasks. giotto-tda streamlines our 
workflow with its efficient functionalities, offers an intuitive interface 
for clear and concise exploration, and benefits from the reliability of a 
well-established library within the TDA field.

# Table of Contents
* Mapper 
* Persistent Homology

# Running code

Please create a virtual environment in terminal and install the required libraries using the included `requirements.txt` file:

#### Linux
```
pip install virtualenv
virtualenv TDA_UAAP
source TDA_UAAP/bin/activate
(TDA_UAAP)$ pip install -r requirements.txt
```

#### Windows
```
pip install virtualenv
python -m venv TDA_UAAP
TDA_UAAP\Scripts\activate
(TDA_UAAP)$ pip install -r requirements.txt
```

#### Jupyter Notebooks
In Jupyter Notebooks software, terminal commands can be run in a notebook cell prepended with the '!' character. For example,
```
!pip install virtualenv
!python -m venv TDA_UAAP
!TDA_UAAP\Scripts\activate
!(TDA_UAAP)$ pip install -r requirements.txt
```

After which, all Jupyter notebooks in this file should be runnable.


## Mapper
This project explores the use of giotto-tda's mapper functionality to 
identify clusters among players in the 84th season of the UAAP 
basketball tournament.


Dataset
We used datasets that contained the following columns: 'Player', 'Team', 'GP', 'Position', 'MPG', 'PPG', 'FGM', 'FGA', 'FG%','3PM', '3PA', '3P%', 'FTM', 'FTA', 'FT%', 'ORB', 'DRB', 'RPG', 'APG', 'SPG', 'BPG', 'TOV', 'PF', '#'.To ensure replicability we suggest structuring the dataset to be used in the same way. But choosing different features might yield varying results.

Required Libraries

giotto-tda: The core library for Topological Data Analysis functionalities.

numpy: Provides numerical computation capabilities.

pandas: Facilitates data loading, manipulation, and potential cleaning/feature engineering before TDA analysis.	

scikit-learn: Offers various tools for data exploration, clustering techniques (like DBSCAN), and dimensionality reduction methods (like PCA) that can be potentially integrated into a custom pipeline (not directly related to giotto-tda's mapper analysis).

Running Mapper using giotto-tda
* Read the csv file containing the basketball data using pandas.
* Run the preprocessing steps.
* Continue with the PCA with or without feature selection.
* Plotting the point cloud is optional
* Define filter function – can be any scikit-learn transformer
* Choose clustering algorithm – default is DBSCAN
* Configure parallelism of clustering step
* Initialise pipeline
* Generate the interactive widget by using the MapperInteractivePlotter
* To analyze the clusters we created additional functions like the find_nodes which gives the name of the player subgroups and the compare_means which compares the average of the node to the league average.


## UAAP Persistence

The "UAAP Persistence" notebook contains our analysis of the UAAP data set using persistent homology. 

Data Preprocessing:

Feature Selection: We selected key features including Points Per Game (PPG), Rebounds Per Game (RPG), Assists Per Game (APG), Steals Per Game (SPG), Blocks Per Game (BPG), and Turnovers (TOV).
Standardization: We standardized these features to ensure comparability and to properly prepare the dataset for topological analysis.

Building the Distance Matrix:

Distance Computation: We calculated a Euclidean distance matrix based on the standardized features. This matrix serves as the foundation for generating the topological structure of the data.

Generating Topological Features:

Rips Complex: Using the RipsComplex from a Python library, we constructed the Rips complex from the distance matrix, depicting the data in a multi-dimensional topological space.
Persistent Homology: We analyzed the Rips complex to identify and track topological features that persist across multiple scales.

Visualization:

Persistence Diagram: This diagram illustrates the 'birth' and 'death' of topological features as the dataset is examined across different scales. Points located far from the diagonal are indicative of significant features.

Persistence Barcode: This visualization shows the persistence of topological features across different scales. Each bar represents a feature, with its length indicating the scale at which the feature persists.






