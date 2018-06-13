# SE and SNL Diagrams: Flexible  data structures for music-based data streams

A softward for generating Start-End and Start-Normalized Length Diagrams from Aligned Hierarchies  for Music-Based Data. 

# Authors
Melissa R. McGuirl, Katherine M. Kinnaird, Claire Savard, Erin Bugbee.

# Contact
For questions/comments please contact Melissa R. McGuirl at melissa_mcguirl@brown.edu.

# About
This software addresses the cover-song task for music-based data. 

# Inputs
This software takes as input a collection of .mat files containing Aligned Hierarchies data stored in variables called 'full_key' and 'full_matrix_no,' where 'full_matrix_no' is a matrix indicating where the repeated structures start and
'full_key' is a vector containing the length of the repeated structures in each row. 
  
# Outputs
Precision and Recall values for mutual k-nearest neighbor matching on SE/SNL diagrams for the cover song task. 

# User options
  1) Wasserstein Inner Norm: Value in [1.0, Infinity]
  2) Wasserstein Outer Norm: Value in [1.0, Infinity] (note, when the outer norm =infinit you are using the Bottleneck metric. In this case the inner norm is automatically set to l-infinity)
  3) Normalization (for run_SNLD.py): 'none' for no mormalization, 'std' for ordinary normalization, or 'cheb' for chebyshev normalization.
  4) Alpha: Scaling parameter alpha, alpha = 1 indicates no scaling.

# Usage
python run_SE.py [-h HELP_MENU] -I INPUT_DIRECTORY -w INNER_NORM -W OUTER_NORM
python run_SNLD.py [-h HELP_MENU] -I INPUT_DIRECTORY -N NORMALIZATION -A ALPHA -w INNER_NORM -W OUTER_NORM

# Dependencies
Hera (available here: https://bitbucket.org/grey_narn/hera.git), Python 2.7, numpy, scipy, sklearn 

# Examples
  1) python run_E.py -I ../data/Thresh01_ShingleNumber6/ -w 2 -W 2  (SE diagrams with 2-2 Wasserstein metric)
  2) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N none -A 0 -w 2 -W 2  (SL diagrams with 2-2 Wasserstein metric)
  3) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N std -A 1 -w 2 -W 2  (SNL diagrams with standard normalization      (M = maximum start time), alpha=1, and the 2-2 Wasserstein metric)
  4) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N cheb -A 10 -w inf -W inf (SNL diagrams with chebyshev normalization, alpha=10, and the infinity-Bottleneck metric)


# Pipeline
  1) Extract start-end diagrams or start-normalized length diagrams from Aligned Hierarchies 
  2) Normalize start times using chebyshev/standard norm (if specified)
  3) Compute Wasserstein or Bottleneck distances between all diagrams in the dataset
  4) Use mutual k-nearest neighbor to pair songs
  5) Generate truth (exanded version of each song pairs with non-expanded version)
  6) Compare to true pairing with SE/SNL mutual-KNN pairing
  7) Compute precision and recall
  
  
# Help
0) python TREE.py -h

FUTURE WORK:
  1) Make sofware flexible for cases where truth is not known
  2) Save mutual knn results to text file 
  
# References and citation for this software 
This accompanying paper for this sofware is:  
- add citation 
For more information on Aligned Hierarchies see: 
-K. M. Kinnaird. Aligned Hierarchies: A Multi-Scale Structure-based Representation For Music-Based Data Streams. Proceedings of the 17th ISMIR Conference, New York City, 2016. 
