This workshop includes a data challenge, wherein we will release a large-scale dataset of images used by politicians, images shared by disinformation agents, and a sample of images shared in otherwise political contexts.
Using this dataset, we are soliciting solutions to address the following challenges:

1. Challenge 1: Identifying Anti-Social Imagery -- Classify images as containing anti-social symbols or presenting an anti-social message. Where possible, provide either explanation or highlighted area of the image associated with the anti-social behavior. Systems will be evaluated on classification performance.

2. Challenge 2: Characterizing Online Influence Campaigns by their Imagery -- While many efforts have worked to characterize influence campaigns (foreign or domestic, inauthentic and authentic), much of these efforts focus on text despite the multi-modal nature of these campaigns. Text is cheaper to produce and analyze, but images are more expensive and more engaging, making images both a potential vector for identifying coordinating accounts and key modality for measuring impact. This challenge asks for systems to use image-characterization methods to classify social media accounts into `authentic` or `campaign` accounts, where the `campaign` label is decomposed into sub-labels across several influence campaigns.

3. Challenge 3: Tracking Screenshot Sharing and Propagation -- As screenshots are increasingly used for reporting quotes and actions of elites across platforms, methods for tracking and attributing these screenshots to individuals are increasingly useful for establishing provenance and propagation paths. To this end, we must first understand how to separate screenshots of duplicate content. Systems submitted for this challenge will identify and cluster duplicate screenshots while being robust to cropping or resizing.


### Data Challenge Posters

Submissions for the data challenge are expected to submit one-page papers describing their approach, which they will then present during the workshop.


### Data Challenge Links

Datasets for these challenges are available via this [link in Google Drive](https://drive.google.com/drive/folders/1T-rMCSjk5C41UTnbp69bC8g9zR5HVVaC?usp=sharing).

This dataset is organized into folders per account, so you get a sample of images per account.
In this folder, you will find:

#### Training Data

- `authenticity.training` - Samples of accounts and associated images across six classes, two authentic groups (`congress` from US Congresspeople and `political_images` from a sample of politically engaged US Twitter accounts) and four inauthentic groups.
- `screenshot.training` - Links to datasets that can be used for training to identify specific screenshots.

#### Challenge Data

- `challenge_data.large` - A large dataset of 2,095 accounts and about 21 images per account. 
- `challenge_data.small` - A small dataset of 411 accounts and about 21 images per account. This dataset is a subsample of the large dataset.

