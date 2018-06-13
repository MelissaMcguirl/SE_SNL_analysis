# SE_SNL_analysis

Start-End and Start-Normalized Length Diagrams for Music-Based Data

# AUTHORS: 
Melissa R. McGuirl, Katherine M. Kinnaird, Claire Savard, Erin Bugbee.

# CONTACT: 
For questions/comments please contact Melissa R. McGuirl at melissa_mcguirl@brown.edu.

# ABOUT: 
This software addresses the cover-song task for music-based data. 

# INPUTS: 
This software takes as input a collection of .mat files containing aligned hierarchies data stored in variables called 'full_key' and 'full_matrix_no,' where 'full_matrix_no' is a matrix indicating where the repeated structures start and
'full_key' is a vector containing the length of the repeated structures in each row. 
  
# OUTPUTS: 
Precision and Recall values for mutual k-nearest neighbor matching on SE/SNL diagrams for the cover song task. 

# USER OPTIONS: 
  1) Wasserstein Inner Norm: Value in [1.0, Infinity]
  2) Wasserstein Outter Norm: Value in [1.0, Infinity] (note, when the outernorm =infinity you are using the Bottleneck metric. In this case the inner norm is also set to l-infinity)
  3) Normalization (for run_SNLD.py): 'none' for no mormalization, 'std' for ordinary normalization, or 'cheb' for chebyshev normalization.
  4) Alpha: Scaling parameter alpha, alpha = 1 indicates no scaling.

# USAGE:
python run_SE.py [-h HELP_MENU] -I INPUT_DIRECTORY -w INNER_NORM -W OUTER_NORM
python run_SNLD.py [-h HELP_MENU] -I INPUT_DIRECTORY -N NORMALIZATION -A ALPHA -w INNER_NORM -W OUTER_NORM

# DEPENDENCIES: 
Hera (available here: https://bitbucket.org/grey_narn/hera.git), Python 2.7, numpy, scipy, sklearn 

# EXAMPLES:
  1) python run_E.py -I ../data/Thresh01_ShingleNumber6/ -w 2 -W 2  (SE diagrams with 2-2 Wasserstein metric)
  2) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N none -A 0 -w 2 -W 2  (SL diagrams with 2-2 Wasserstein metric)
  3) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N std -A 1 -w 2 -W 2  (SNL diagrams with standard normalization      (M = maximum start time), alpha=1, and the 2-2 Wasserstein metric)
  4) python run_SNLD.py -I ../data/Thresh01_ShingleNumber6/ -N cheb -A 10 -w inf -W inf (SNL diagrams with chebyshev normalization, alpha=10, and the infinity-Bottleneck metric)


# CURRENT PIPELINE:
  1) Extract start-end diagrams or start-normalized length diagrams from aligned hierarchies 
  2) Normalize start times using chebyshev/standard norm (if specified)
  3) Compute Wasserstein or Bottleneck distances between all diagrams in the dataset
  4) Use mutual k-nearest neighbor to pair songs
  5) Generate truth (exanded version of each song pairs with non-expanded version)
  6) Compare to true pairing with SE/SNL mutual-KNN pairing
  7) Compute precision and recall
  
  
# HELP: 0) python TREE.py -h

FUTURE WORK:
  1) Make sofware flexible for cases where truth is not known
  2) Save mutual knn results to text file 
  
# REFERENCE AND CITING THIS SOFTWARE
This accompanying paper for this sofware is:  
- add citation 
  
