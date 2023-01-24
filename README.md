<h1 align='center'>Monet Painting Generation</h1>
<h4 align='center'> Mircea Gosman:<br> mircea.gosman@mail.mcgill.ca <br>
Arno Douady:<br> arno.douady@epfl.ch</h4>

---

<div align="center">
   
| Modern Photograph | Generated Painting | Modern Photograph | Generated Painting |
| :-------------: | :-------------: | :-------------: | :-------------: |
| <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-339-photo.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-339-paint.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-277-photo.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-277-paint.png" width="140"> |
| <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-203-photo.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-203-paint.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-68-photo.png" width="140"> | <img src="https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Results/Cycle_GAN_500/training-output/trained-68-paint.png" width="140">  |

</div>

---

## Scope
This project was elaborated within the scope of the class: ECSE 526: Artificial Intelligence (Fall 2022, McGill University). More details can be found in our [paper report](https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Paper.pdf).

## Abstract
<i>The goal of this project in artificial
intelligence is to develop a Generative Adversarial
Network (GAN) to create new paintings in the style of
the French painter Claude Monet. In this [paper](https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Paper.pdf), we
describe how our DC, SN, and Cycle GANs tackle problem and
discuss the issues we encountered.</i>

## Repository Content 
This repository contains the [report](https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Paper.pdf), samples of the best [results](https://github.com/Mircea-Gosman/AI_Term_Project/tree/master/Results) of each of our models, and the [Jupyter notebooks](https://github.com/Mircea-Gosman/AI_Term_Project/tree/master/Models) from which were produced these results.

## Code
This project is not made of a single entry point. This is because generative networks require high end computational ressources (GPUs) and we could only access such ressources through the Jupyter-powered Kaggle platform. Consequently, each of our models stands as a single program in its individual Jupyter notebook. To run one a model ([e.g.](https://github.com/Mircea-Gosman/AI_Term_Project/blob/master/Models/SN-GAN.ipynb)), import as a Notebook from a new Kaggle project. Import the dataset from the [Monet Kaggle competition](https://www.kaggle.com/competitions/gan-getting-started) Then, make sure to activate accelerated hardware by selecting a GPU before running the code.

Each model's parameters can be tweak its notebook's config section (DC & SN-GANs) or from its training loop (Cycle GAN). Running a notebook will import & repartition the data, create the GAN and its submodels, train the GAN (which might take from a couple of minutes to a few hours), and produce a TAR downloadable TAR file with the results. The Sliced Wasserstein Distance of the run is made available in the `Predict` section's `CLI`.

## Results
The TAR file that contains a model's results consists of a few subdirectories. The important ones are,
* for the DC & SN-GANs:
    * `/training-output`: The generated paintings from noise input at each training epoch, labeled as `trained-{epoch}-fake.png`
    * `/test-output` : 15 generated paintings from noise input with the final trained model, labeled as `test-{epoch}-fake.png`. 
* for the cycle GAN:
    * `/training-output`: The generated paintings (`trained-{epoch}-paint.png) and the corresponding photograph input (`trained-{epoch}-photo.png`)
    * `/test-output/generated_paintings`: The final output of the paintings generator (`trained-{epoch}-paint.png`) from dataset photographs (`trained-{epoch}-photo.png`)
        
The rest of the subfolders, if existant, are artifacts of previous procedures and can be discarded.

## Acknowledgement
We have used a selection of online tutorials to help us understand how to build the various model within the ml library ecosystem. 

* For the DC & SN GAN architecture: 
    * [Starting out with GANS](https://towardsdatascience.com/generating-modern-arts-using-generative-adversarial-network-gan-on-spell-39f67f83c7b4)

* For the Cycle GAN:
    * [Patch Discriminator](https://machinelearningmastery.com/how-to-develop-cyclegan-models-from-scratch-with-keras/)
    * [Combining the models](https://machinelearningmastery.com/cyclegan-tutorial-with-keras/) for training with cycle consistency loss
