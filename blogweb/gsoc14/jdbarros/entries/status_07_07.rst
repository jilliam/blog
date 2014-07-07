.. blogpost::
  :title: 3. Experiments and results. Part 1.
  :author: jilliam
  :date: 07-07-2014

  **DESCRIPTION**
  
  Today I will present some results obtained with the new algorithm, based on [Min1]_, vs. the methods that are already implemented in the module:
  1. Block-based algorithm. 
  2. Adaptive Cost 2-pass Scanline Optimization, based on [Wang06]_.

  The experiments were performed using four pair of images from the Middlebury dataset: Cones, teddy [Scharstein03]_, tsukuba and venus [Scharstein02]_. The general parameters used to test the algorithms were set as follows:
    
  * Radius of the matching window: 5.
  * Size of set of disparity hypotheses: 60.
  * Horizontal offset: 0.

  The adaptive cost scanline optimization algorithm and the new implementation required the tuning of extra parameters.
  For the first method, the used values were:

  * Spatial bandwidth for cost aggregation: 25.
  * Color bandwidth for cost aggregation: 10.
  * Weak smoothness penalty cost: 20.
  * Strong smoothness penalty cost: 100

  On the other hand, the following parameters were set in the new method:

  * Radius of noise-suppresion filter, filter_radius: 0, 2 and 5.
  * Number of the subset of the disparity hypotheses, num_disp_candidates: 30 and 60.
  * Weak smoothness penalty cost: 20.
  * Strong smoothness penalty cost: 100
  
  No additional pre or post-processing methods were used during the experiments.

  **RESULTS**
  
  The results obtained for the set of images are presented in Fig. 1-4: (a) Original images, (b) ground truth maps, (c) results of adaptive cost scanline optimization, (d) results of block-based algorithm. Results of new method with (e) Weights = 1, num_disp_candidates = 60, filter_radius = 0; Weights computed using [Yoon06]_ and (f) num_disp_candidates = 60, filter_radius = 0, (g) num_disp_candidates = 30, filter_radius = 0, (h) num_disp_candidates = 30, filter_radius = 2, (i) num_disp_candidates = 30, filter_radius = 5.

  **Fig. 1. Cones**
  .. image:: figures/Cones.png
	      :height: 240px
	      :align: center

  **Fig. 2. Teddy**
  .. image:: figures/Teddy.png
	      :height: 240px
	      :align: center

  **Fig. 3. Tsukuba**
  .. image:: figures/Tsukuba.png
	      :height: 240px
	      :align: center

  **Fig. 4. Venus**
  .. image:: figures/Venus.png
	      :height: 240px
	      :align: center
  
  In the next post, I will present more experiments with the current dataset. Moreover, a quantitative evaluation of the method will be performed using the ground truth data.

  During the following days I will also be improving the code to reduce the run time.

  **REFERENCES** 

  .. [Scharstein02] D. Scharstein and R. Szeliski. A taxonomy and evaluation of dense two-frame stereo correspondence algorithms. International Journal of Computer Vision, 47(1/2/3):7-42, April-June 2002.

  .. [Scharstein03] D. Scharstein and R. Szeliski. "High-accuracy stereo depth maps using structured light". In IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR 2003), volume 1, pages 195-202, Madison, WI, June 2003.




