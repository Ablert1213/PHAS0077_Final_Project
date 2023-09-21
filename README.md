# PHAS0077_Final_Project

## Documentation for the Statistical Analysis of `49Ti_16O` and `12C_1H4` Datasets

## Overview

The files in this repository are designed to conduct statistical analysis on the first digits of datasets to test their distribution against Benford's Law. The primary datasets for this study are the isotopologues of Titanium Monoxide and Methane from the ExoMol database, which can be accessed [here](https://www.exomol.com/data/molecules/).

For the Titanium Monoxide dataset (`49Ti_16O`), four distinct experiments were conducted:

1. **Direct Analysis of the Entire Dataset**: This approach directly analyses the entire dataset without any segmentation.
  
2. **Transform Dataset (`49Ti_16O_TransformDataset`)**: This experiment transforms the original dataset into a form that would more closely resemble a uniform distribution on a logarithmic scale.

3. **Split Dataset (`49Ti_16O_SplitDataset`)**: Two sub-experiments were conducted here:
   - The first experiment involved segmenting the dataset based on the frequencies of the logarithmic values. The goal was to group numbers with similar frequencies together. This approach aimed to retain as much of the original dataset's magnitude as possible. The dataset was divided into eight groups, each containing numbers with similar frequencies.
   - The second experiment took a different approach by dividing the dataset into equal groups without preserving the magnitude of the original numbers. This segmentation was purely based on trying to achieve a uniform distribution on a logarithmic scale for groups in the middle.

4. **Excluding Extremes (`49Ti_16O_ExcludingExtremes`)**: The third experiment focused on refining the dataset by excluding extreme numbers and tail values. The basic logic behind this approach was to eliminate potential outliers or extreme values that might skew the distribution and influence the results.

Despite the variations in the segmentation approaches, none of the experiments yielded results that were more aligned with Benford's Law than when analyzing the entire dataset as a whole.

For the Methane isotopologues (`YT10to10` and `YT34to10`):

1. Due to the substantial size of these datasets, their distribution plots were generated separately in the `_Dist.ipynb` files.
2. The `_AnalyseDataset.ipynb` files directly analyze the entire dataset.
3. The `_ChopFile.ipynb` files analyze the dataset in two ways: 
   - Analyzing each individual file.
   - Analyzing groups of 10 files together.

The primary goal of these analyses is to determine if the leading digits of the data in these datasets follow Benford's Law, a principle that describes the frequency distribution of leading digits in many real-life sets of numerical data.

## Results Visualization (`12C_1H4_Results_plot.ipynb`)

This Jupyter Notebook is dedicated to visualizing the results obtained from the `_ChopFile.ipynb` notebooks. It reads the results from text files and plots the Chi^2 and p-values for each file or group of files. Additionally, it visualizes the Mean Absolute Deviation (MAD) values for each file or group of files, providing a clear representation of the conformity of the datasets to Benford's Law.

The notebook contains the following sections:

1. **Visualization of Chi^2 and p-values for individual files in `10 to 10`**.
2. **Visualization of Chi^2 and p-values for groups of 10 files in `10 to 10`**.
3. **Visualization of Chi^2 and p-values for individual files in `34 to 10`**.
4. **Visualization of Chi^2 and p-values for groups of 10 files in `34 to 10`**.
5. **Visualization of MAD values for individual files in `10 to 10`**.
6. **Visualization of MAD values for groups of 10 files in `10 to 10`**.
7. **Visualization of MAD values for individual files in `34 to 10`**.
8. **Visualization of MAD values for groups of 10 files in `34 to 10`**.

Each section reads the respective results from a text file, extracts the necessary data, and plots it using `matplotlib`. The plots provide a clear visual representation of the conformity of the datasets to Benford's Law, with threshold lines indicating different levels of conformity.

## Prerequisites

### Dependencies

To run these notebooks, you'll need the following Python libraries:

- `pandas`: For data manipulation and analysis.
- `numpy`: For numerical operations.
- `scipy`: For scientific computations.
- `matplotlib`: For plotting and visualization.
- `bz2`: For working with bz2 compressed files.
- `glob`: For file operations.
- `os`: For operating system dependent functionality.
- `re`: For regular expressions.

You can install these libraries using `pip`:

```bash
pip install pandas numpy scipy matplotlib re
```

### Data

The datasets for this analysis are extremely large and are hosted on the ExoMol Server. The datasets are located in the repository at `/mnt/data/exomol/exomol3_data/`. Due to the size and hosting constraints, sample data/input files for local testing are provided on GitHub. These sample files are randomly extracted from the TiO dataset files.

## Running the Notebooks

1. **Environment Setup**: It's recommended to set up a virtual environment to avoid any dependency conflicts. Use `conda` to create a new environment.

2. **Launching Jupyter Notebook**: Navigate to the directory containing the notebooks and launch Jupyter Notebook:

```bash
jupyter notebook
```

3. **Running a Notebook**:
   - Open the desired notebook from the Jupyter dashboard.
   - **For Running Sample Files on GitHub**: Uncomment the lines that retrieve the sample input files and comment out the lines that retrieve the full dataset. Specifically:
     ```python
     # For sample input
     # get current repository
     current_directory = os.getcwd()
     filenames =

 [os.path.join(current_directory, '*.trans.bz2')]
     # For full dataset
     # filenames = glob.glob('/mnt/data/exomol/exomol3_data/49Ti-16O/LYT10to10/*.bz2')
     ```
   - Click on `Kernel` -> `Restart & Run All` to run the entire notebook.

4. **Viewing Results**: The results will be displayed within the notebook itself. For visualizations, plots will be demonstrated.

## Conclusion

The analysis conducted on the datasets provides a comprehensive understanding of the distribution of the leading digits in the datasets. The visualizations in the `12C_1H4_Results_plot.ipynb` notebook offer a clear representation of the conformity of the Methane dataset to Benford's Law. The results can be used to draw conclusions about the authenticity and reliability of the datasets, as datasets that conform to Benford's Law are often considered to be free from human tampering or manipulation.
