## Method Description

Image Generator for Tabular Data (IGTD) is an algorithm that transforms tabular data into images. The algorithm assigns each feature to a pixel in the image. As a result of this assignment, the algorithm generates an image for each data sample, in which the pixel intensity reflects the value of the corresponding feature in the sample. The algorithm searches for an optimized assignment of features to pixels by minimizing the difference between the ranking of pairwise distances between features and the ranking of pairwise distances between the assigned pixels, where the algorithm calculates the distances between pixels based on their coordinates in the image. Minimizing the difference between the two rankings assigns similar features to neighboring pixels and dissimilar features to pixels that are far apart. The algorithm achieves optimization through an iterative process of swapping the pixel assignments of two features. In each iteration, the algorithm identifies the feature that it has not considered for swapping for the longest time, and seeks a feature swapping for it that reduces the difference between the two rankings most.   


## Frequently Asked Questions

| Question | Answer |
| ------------- | ------------- |
| Is the method generally applicable to any type of data? | Yes, users can apply it to any type of tabular data. |
| Are there any constraints on the size of the data (minimum, maximum)? | No. However, if there are too few features and samples, it is not practically meaningful to apply the algorithm. |
| Are there any specific parameters or statistical characteristics in the input data that need to be present for the algorithm to work? | The algorithm requires several input parameters, as explained by the comments in the provided scripts. The user needs to have basic knowledge about the IGTD algorithm to use the package, and the linked IGTD publication. |
| Can users generate an image in 3D, or 1D, or other dimensions? | Yes. IGTD is very flexible. The current implementation covers 1D and 2D, and users can extend the algorithm to 3D. |

## Setup

To set up the Python environment needed to run this algorithm:
1. Install [conda](https://docs.conda.io/en/latest/) package manager.
2. Clone this repository.
3. Enter the Scripts directory.
4. Create the environment as shown below.
    ```
    conda env create -f environment.yml -n IGTD
    conda activate IGTD
    ```
5.  Run the [./Example_Run.py](./Example_Run.py) script for a demo. 

This demo runs the IGTD algorithm using two configurations. The first configuration uses the Euclidean distance for calculating pairwise feature distances and pairwise pixel distances and the absolute function for evaluating the difference between the feature distance ranking matrix and the pixel distance ranking matrix. The first configuration saves the result in [../Results/Test_1](../Results/Test_1) folder. That folder also contains some sample results.

The second configuration runs the IGTD algorithm using the Pearson correlation coefficient for calculating pairwise feature distances, the Manhattan distance for calculating pariwise pixel distances, and the square function for evaluating the difference between the feature distance ranking matrix and the pixel distance ranking matrix. The second configuration saves the result in [../Results/Test_2](../Results/Test_2) folder. That folder also contains some sample results.

The sample output from Example_Run.py shows the conversion of the algorithm for the two configurations described above: 

```
python Example_Run.py
Step 0 err: 54021791215.0
.....
Step 5165 err: 25092527089.0
Step 0 err: 1.0993404642421798e+16
....
Step 4488 err: 3518731791808334.0
```



## Use IGTD to Convert Tabular Data into Images

The [./IGTD_Functions.py](./IGTD_Functions.py) script provides all the functions used by the IGTD algorithm. For explanations about the inputs and outputs of all functions, refer to comments in the script. The table_to_image function is the main function for running the IGTD algorithm. The min_max_transform function preprocesses input data, scaling the minimum and maximum values of each feature linearly to 0 and 1, respectively. 

The [Example_Run.py](./Example_Run.py) script provides examples demonstrating how to use the functions for running the IGTD algorithm. 
