<a name="readme-top"></a>

<img src="merger-train-logo.png" alt="Logo" width="80" height="30">

### Example code for interfacing with [the data](https://www.canfar.net/storage/vault/list/AstroDataCitationDOI/CISTI.CANFAR/23.0031/data) from [Wilkinson et al. (2024)](https://arxiv.org/abs/2401.13654): The limitations (and potential) of non-parametric morphology statistics for post-merger identification ###

Images and example code from [Wilkinson et al. (2024)](https://arxiv.org/abs/2401.13654) for the purposes of training models to detect mergers and non-mergers. In an associated repository are random forest and LDA models trained on SKIRT images of mergers and non-mergers from IllustrisTNG100-1, as well as the necessary data to train your own. The code in */Example/* should help get you started with interfacing with this data.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#description-of-data-products">Description of Data Products</a>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments and How to Cite</a></li>
  </ol>
</details>


<!-- DESCRIPTION OF DATA -->
## Description of Data Products

TThis repository contains four directories that constitutes the products, training data, and trained models used in our work:

1. Photometry

    This directory contains the raw output from the SKIRT imaging pipeline, i.e. the r-band photometry generated by the SKIRT, before any realism is applied. Native to the SKIRT pipeline, the images have a resolution of pixel scale of 0.1 kpc / pix and are redshifted according to a fixed redshift of z = 0.1. The SKIRT output is organized by the snapshot number from which the mergers and controls are drawn from the simulation. Since mergers have a non-uniform distribution with simulation redshift/snapshot, there are varying number of mergers in each snapshot zip file. Furthermore since there is a +/- 1 snapshot tolerance in control matching, there is no guarantee that the number of mergers and controls in a given snapshot is equal. Within the zip file, individual files are labelled according to their snapshot and subhaloID.
    
2. Idealized

    This directory contains the "idealized" images. Idealized images have been run through our realism pipeline (e.g. have been rebinned to a pixel scale of 0.1 arcsec / pix) but with minimal sky noise (sigma_sky = 30 mag arcsec^-2) and no PSF blurring. The zip file in this directory contains 3,392 images comprised of 424 mergers and 424 non-merger controls matched in mass and redshift, each of which are viewed from four unique viewing angles (indicated by v0, v1, v2 or v3 in their file names).
    
3. Degraded

    This directory contains realistic images degraded to various image qualities. There are 36 combinations of depth (via sigma_sky) and seeing (via PSF FWHM) and each zip file is labelled accordingly. Like the idealized zip file, the zip files in this directory contain 3,392 images each. 
    
4. TrainedModels

    This directory contains trained random forest (RF) and linear discriminant analysis (LDA) models for each image quality in the Degraded and Idealized directories. The models are saved as "pickled" Python objects and can be loaded into Python with the pickle package: https://docs.python.org/3/library/pickle.html
    
    
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage

Data can be downloaded directly from the web repository. A more sophisticated approach is to use the vos file management system. Documentation on vos can be found here: https://pypi.org/project/vos/

An example of a vos download to your local system would be:

    vcp vos:/AstroDataCitationDOI/CISTI.CANFAR/23.0031/data/Degraded/IllustrisTNG100-1_depth=26_psf=0.75_filter=CFHT_MegaCam.r.tar.gz ./
    
Then the zipped data can be extracted using tar:

    tar -xvf ./IllustrisTNG100-1_depth=26_psf=0.75_filter=CFHT_MegaCam.r.tar.gz

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Scott Wilkinson - swilkinson@uvic.ca

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgements and How to Cite

If you use the images to train your own data, I kindly ask that you cite the following:

* [Bottrell et al. (2019)](https://ui.adsabs.harvard.edu/abs/2019MNRAS.490.5390B/abstract)
* [Bottrell et al. (2023)](https://ui.adsabs.harvard.edu/abs/2024MNRAS.527.6506B/abstract)
* [Wilkinson et al. (2024)](https://arxiv.org/abs/2401.13654)
* [Byrne-Mamahit et al. (submitted)]

You may also wish to cite the IllustrisTNG collaboration for use of their data:

* [Springel et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018MNRAS.475..676S/abstract)
* [Nelson et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018MNRAS.475..624N/abstract)
* [Naiman et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018MNRAS.477.1206N/abstract)
* [Pillepich et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018MNRAS.475..648P/abstract)
* [Marinacci et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018MNRAS.480.5113M/abstract)

and the creators of SKIRT and SKIRT 9:

* [Camps & Baes (2015)](https://ui.adsabs.harvard.edu/abs/2015A%26C.....9...20C/abstract)
* [Baes (2020)](https://ui.adsabs.harvard.edu/abs/2020MNRAS.494.2912B/abstract)

For more information, visit [the IllustrisTNG cite](https://www.tng-project.org/) and [the SKIRT9 documentation](https://skirt.ugent.be/root/_home.html).

<p align="right">(<a href="#readme-top">back to top</a>)</p>


