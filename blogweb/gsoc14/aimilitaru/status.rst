My status updates
=================


  :nr_days: 60
  :author: aimilitaru



  :title: Face Shift ( First phase )
  :author: aimilitaru
  :date: 18-06-2014

        * **Project Overview**

                The goal of this project is to implement a program that will modify the expressions of several scanned faces according to the facial expressions captured by a RGBD camera.

		The first step is to create a statistical model based on a training database of faces. The training set used so far was the one provided by the FaceWarehouse project and it consisted of 3D meshes stored in **.obj** files. For further information, please consult the following link: http://gaps-zju.org/facewarehouse/

        * **Aproach**

		- For each face in the training set, a column vector *S* was created and it contained the coordinates for every vertice of the mesh. Afterwards, the avearage vector and the covariance matrix were calculated. 
		- Normally, the covariance matrix would be calculated as |cov|, however one should note that this matrix is 34530 by 34530 and in order to compute the statistical model, the most significant eigenvectors are required. To speed up the calculations, a matrix **T** was formed by joining the |vec| vectors and the eigenvectors for |tra| were calculated. It is important to note that the size of |tra| is determined by the number of faces and that the eigenvectors of the covariance matrix can be obtained by left multiplying **T** to the eigenvectors of |tra|.
		- Once the eigenvectors are calculated, the statistical model is obtained according to the formula: |form|, where |alpha| is the weight of an eigenvector, determined by multiplying a random number in the range **[-1,1]** with the corresponding eigenvalue.
		- The final results of this phase are presented below. The average face is:



                .. image:: images/snapshot01.png
                        :width: 650px
                        :height: 300px
                        :align: center

		- And the model is:


                .. image:: images/snapshot00.png
                        :width: 650px
                        :height: 300px
                        :align: center

		- As you can see, the model obtained is a bit flattened compared to the mean face, that is because in the training set the majority of the faces are a bit rounded, however this project needs a model to take into consideration several types of faces, and this is why we need to consider the covariance of the samples in the database.


        * **Feature Steps**

		- For this model, only the vertices of the faces were used, however the texture coordinates also need to be taken into consideration. Unfortunately, the database does not provide any information about the colors as of yet. Once the data is available the model needs to be adapted for this feature
		- Once the statistical model is fully configured, a 3D registration algorithm must be applied to project the facial expression of a testing sample to the model. 

        * **References**

		- T. Vetter and V. Blanz. A Morphable Model For The Synthesis Of 3D Faces. Max-Planck-Institut, Tubingen, Germany






		.. |cov| image:: images/CodeCogsEqn.gif
		.. |vec| image:: images/CodeCogsEqn1.gif
		.. |tra| image:: images/CodeCogsEqn2.gif
		.. |alpha| image:: images/CodeCogsEqn3.gif
		.. |form| image:: images/latex1.jpg
		.. |avg| image:: images/snapshot01.png
		.. |model| image:: images/snapshot00.png


