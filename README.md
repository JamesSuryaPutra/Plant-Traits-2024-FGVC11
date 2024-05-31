# PlantTraits2024 - FGVC11

# Overview
We welcome you to PlantTraits2024 Challenge, an exciting part of the FGVC11 workshop at CVPR 2024, where you have the chance to personally contribute to advance our understanding of the global patterns of biodiversity. Our goal is to predict a broad set of 6 plant traits (e.g. leaf area, plant height) from crowd-sourced plant images and some ancillary data.

# Why does it matter?
Think of plants as the superheroes of our ecosystems. Their traits hold the key to understanding ecosystems, e.g., in terms of their diversity, productivity, or how these green heroes face the challenges brought on by climate change. By solving this competition effectively, you become a superhero, too; contributing to our understanding of how plants navigate the complexities of climate change.

By analyzing thousands of plant images acquired by citizens, participation in this competition is a chance to be a part of something bigger and help us uncover the properties of our ecosystems. Are you ready for the mission?

# Description
This competition aims to predict plant properties; so called plant traits, from citizen science plant photographs. Why are plant traits currently so relevant? Plant traits are plant properties that are used to describe how plants function how they interact with the environment. For instance, the trait of plant canopy height indicates how good a plant is at overshadowing its neightbors in the competition for sun light. Robust leaves (indicated by the leaf mass pear leaf area) indicate that plants optimize towards extreme conditions, such as heavy winds or droughts. Yet, environmental conditions are not static. Due to global change, the biosphere is being transformed at accelerating pace. Especially climate change is assumed to drastically impact the functioning of the ecosystems. This includes several processes, e.g. adaptions of plants and their traits to new conditions or even a altered plant species distribution with a resulting modification of the distribution of plant traits. However, we can hardly project on a global scale how plant traits and as such entire ecosystems will react to climate change because we do not have sufficient data on plant traits.

A data treasure in this regard may be the growing availability of citizen science photographs. Thousands of citizens around the globe photograph plants with species identification apps (examples are iNaturalist or Pl@ntNet). The species are identified using AI algorithms, and the prediction, photograph, and geolocation are curated in open databases. There are already more than 20 million plant photographs available, covering all ecosystem types and continents.

In its original form, this data initially only provides information on the species name of a plant and not its traits. However, a pioneering study showed that artificial intelligence can predict plant traits from such photographs using Convolutional Neural Networks (Schiller et al., 2021). To achieve this, we paired sample images from the iNaturalist database with plant trait data that scientists have been curating for decades for various species. The challenge was that the images and plant trait observations were not acquired for the same plant individuals or at the same time. Nevertheless, using a weakly supervised learning approach, we trained models that demonstrated the potential of this approach for a few plant traits. However, this potential was evident only for a limited number of plant traits and a couple of thousand images. This competition aims to further unlock the potential of predicting plant traits from plant photographs. To achieve this, we gathered more training data (over 30,000 images with labels).

Find here the original article:
Schiller, C., Schmidtlein, S., Boonman, C., Moreno-Martínez, A., & Kattenborn, T. (2021). Deep learning and citizen science enable automated plant trait predictions from photographs. Scientific Reports, 11(1), 16395. (https://www.nature.com/articles/s41598-021-95616-0)

The interested reader may also see these references for some background and the general idea:
- Wolf, S., Mahecha, M. D., Sabatini, F. M., Wirth, C., Bruelheide, H., Kattge, J., … & Kattenborn, T. (2022). Citizen science plant observations encode global trait patterns. Nature Ecology & Evolution, 1-10. (https://www.nature.com/articles/s41559-022-01904-x)
- Moles, A.T., Xirocostas, Z.A. Statistical power from the people. Nat Ecol Evol 6, 1802–1803 (2022). (https://www.nature.com/articles/s41559-022-01902-z)

# Competition
The primary objective of this competition is to employ deep learning-based regression models, such as Convolutional Neural Networks (CNNs) like ConvNext or Transformers, to predict plant traits from photographs. These plant traits, although available for each image, may not yield exceptionally high accuracies due to the inherent heterogeneity of citizen science data. The various plant traits describe chemical tissue properties that are loosely related to the visible appearance of plants in images. Despite the anticipated moderate accuracies, the overarching goal is to explore the potential of this approach and gain insights into global changes affecting ecosystems. Your contribution to uncovering the wealth of data and the distribution of plant traits worldwide is invaluable.

To enhance model performance, consider implementing the following strategies:
- Multi-task learning scheme
Implement a multi-task learning approach where the model predicts multiple plant traits simultaneously from photographs. This enables the model to capture relationships between different plant traits, potentially boosting overall performance. Predicting all traits at once is considered the most promising approach.
- Integration of ancillary geodata
In a pioneering study (Schiller et al. 2021), climate information was integrated based on the photograph's location, recognizing the significant impact of temperature, precipitation, and seasonality on plant growth. For this competition, besides climate data (derived from worldclim), additional ancillary predictors from various geodatasets are provided, including multitemporal optical and radar satellite data (MODIS, VOD, respectively), and soil information. These predictors are intended to supplement plant photographs, offering valuable contextual information. Explore the potential of training a multi-modal model where predictors include a plant image along with a single vector combining all ancillary information or multiple vectors for each information set (climate data, soil data, satellite data). Refer to the 'Data' section for detailed information on datasets.
- Ensembles
It may also be promising to test model ensembles (different CNN backbones in combination), given that four eyes see more than one.

Your contribution in exploring and utilizing this diverse set of data will not only advance the field but also contribute significantly to understanding the broader implications of global changes on ecosystems. Your efforts in this competition will help uncover valuable insights from the wealth of citizen science data.

# Evaluation
The models will be evaluated against the independent test data. The evaluation metric for this competition is the mean R2 over all 6 traits. The R2 is commonly used for evaluating regression models and is the ratio of the sum of squares the residuals (SSres) to the total sum of squares (SStot).

The R2 can result in large negative values. To prevent that we will only consider R2 values > 0.

The submission should include a .csv file with a prediction for each trait and the following columns: id (see labels) and a prediction for each trait (X1080, X50, …). An example is given with 'sample_submission.csv'.
