---
layout: page
permalink: /ASCEP/
title: <b>S</b>tatistical <b>A</b>nalysis for <b>B</b>iological <b>I</b>mage <b>D</b>ata
description: 2023 • Institute of Statistical Science, Academia Sinica
logo: /assets/img/AcademiaSinica.png
news: true
---

### A Speedy and robust Cryo-EM processing Platform (ASCEP)
With the recent advance in the equipment together with GPU-accelerated computations and enhancement of algorithms, Cryo-electron microscopy (cryo-EM) has become a mainstream technique to solve structures of macro-molecules at near-atomic resolution. However, further extending to atomic resolution has been hindered by both the noisy nature of the recorded images and the heterogeneity of samples. Enhancement of the signal-to-noise Ratio (SNR) and differentiate the conformation states of these images are thus the keys for solving higher resolution 3D structure. Here, a Speedy and robust Cryo-EM processing Platform (ASCEP) based on Scipion developed by our team is proposed. It contains a cleaner interface and provides novel algorithms from our team.



### Rapid Alignment with Moment of Inertia
Moment of Inertia (MoI) as a 2 by 2 matrix I containing the central moments with order two, whose first eigenvector corresponds to the object’s orientation, has been a popular tool for image alignment (Jan, Suk and Zitová, 2016). However, the low SNR nature of cryo-EM images has prevented the direct application of MoI. We proposed an algorithm called Rapid Alignment with Moment of Inertia (rAMI), and we show that it can be widely applicable to the current alignment steps in cryo-EM. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/MOI2.PNG' | relative_url }}" alt="" title="example image"/>
    </div>
</div>


### Dimension Reduction and Image Clustering
In contrast to X-ray crystallography, cryo-EM does not need crystals but can view dispersed biological molecules embedded in a thin layer of vitreous ice. The electron beam transmitting through the specimen generates two-dimensional projections of these freely oriented molecules and the 3-D structure can be obtained by back projections provided the angular relationships among them are determined.

As biological molecules are highly sensitive to electron beams, only very limited doses are allowed for imaging. This yields a barely recognizable image for an individual molecule. Nevertheless, as the molecule has high symmetry, for example an icosahedra virus, the symmetry would facilitate the image processing and allow for attaining atomic resolution structure. However, the de-noising for a particle of low or no symmetry is evidently challenging as it requires the alignment and clustering of many images of the same orientations for averaging.

Usually this task implies that a very large number of images are to be collected as each cluster of sufficient number of images is on demand for attaining near-atomic resolution. These images represent the projections of the same molecules with randomized translations and rotations, and free orientations. In order to determine the angular relationship among orientations for deriving the 3-D reconstruction, it is crucial to align the images and cluster them into classes of similar orientations. The alignment is aimed to register the images into the same molecular coordinates, and the representative image of each cluster will achieve some level of  denoising through averaging.

We have investigated two related statistical problems, the dimension reduction and the clustering algorithm. We employed the Two Stage Dimensional Reduction (2SDR) to do the dimension reduction for thousands of the cryo-EM images simultaneously and a clustering algorithm γ-SUP for image clustering.  Moreover, To deal with the random orientation nature of the particle, a 2D classification algorithm called Distributed Robust Multi-Reference Alignment (DRMRA) that combines alignmnet is developed. This approach not only leads satisfactory clustering accuracy but also saves a huge amount of computation time.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/about-1.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>

### Denoising and Preprocessing
Besides developing our own 2D clustering algorithm, we also introduce a simple, fast and loss-less pre-processing strategy, based on 2SDR, to initialize 2D clustering.  By implementing this 2SDR pre-processor prior to representative clustering algorithms, RELION and ISAC, we compare the performances with and without the pre-processor. Tests using multiple cryo-EM experimental datasets reveal the pre-processor gives benefits of saving the time on clustering, increasing the yield of particles, and improving the quality of classes. Remarkably, test with a huge dataset of 80S ribosome demonstrates the cost of the pre-processing is low while re-sifting a TRPV1 ion-channel dataset with the aid of the pre-processor has lifted the overall resolution of 3D structure by up to 0.2 Angstrom with concomitant enhancement in the interpretability of map. Our findings suggest the 2SDR pre-processor, with light computation, is applicable for boosting the performance of 2D clustering algorithms.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/about-2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>

### Random partition t-SNE and Interactive t-SNE
Data visualization has been recognized as an important tool in exploring the heterogeneity of high dimensional data, for which many statistical methods have been used including Principal Component Analysis (PCA), Multidimensional Scaling (MDS) and Laplacian Eigenmaps. Along with the development of data visualization methods, t-Distributed Stochastic Neighbor Embedding (tSNE) proposed in 2008 by Laurens van der Maaten and Geoffrey Hinton has been the first to successfully separate the 10 digit groups of MNIST data set into 10 clusters, yielding a total of 5997 citations to date. There are two key features in tSNE for its success: 1) it transforms the similarity matrix into a distribution (e.g. Gaussian distribution and T-distribution) for both the input data of high dimension and the visualization in two dimensions; 2) it minimizes the KL divergence between these two distributions by the gradient descent algorithm. However, as the data volume becomes huge, the computation for similarity matrix becomes a burden and the application faces an overwhelming barrier. Here, we propose a random partition algorithm for t-SNE, which we name RP-tSNE, to accommodate large volume data sets for data visualization. In addition to providing a proof for the consistency of RP-tSNE, we will demonstrate that it can be applied to real-data analysis that can validate the 2D clustering results. Finally, we further design an interactive version of t-SNE to fine-tune the clustering results that has the possibility to find more views and conformations after clustering.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/about-3.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>

### Analyzing Model Bias in Cryo-EM Analysis
Meaningful 2D clustering depends on good image alignment, for which all possible rotations and translations are exhaustively searched to find the most fitted solution. However, image alignment for highly noisy data can be strongly biased toward the reference model, which is referred as model bias phenomenon. Here, we show how we investigate model bias from a mathematical and statistical perspective. We propose an index to quantify model bias and provide the consistency and asymptotic theorems. The results may be further applied to set a threshold to perform particle filtering.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/about-4.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>



<h3>Software</h3>

 ▪ <strong> ASCEP </strong> : Cryo-EM analysis software that includes <strong> Pre-Pro </strong> and <strong> 2SDR </strong> . Downloaded is available <a href="https://docs.google.com/forms/d/e/1FAIpQLSfITYqUDG3SSN5p0gcikULWgNfiSpO-Zmf-wr9C-_zrbBWvvQ/viewform">
   here
  </a>.<br/>
 ▪ <strong> Cryo-RALib</strong> : A library that for accelerating alignment which is under development. The current version can be found <a href="https://github.com/phonchi/Cryo-RAlib">
   here
  </a>.


  <h3>Resources</h3>
   ▪ <strong> Resource</strong> : Check out for other computational cryo-EM methods <a href="https://github.com/phonchi/Computational-CryoEM">
   here
  </a>.






