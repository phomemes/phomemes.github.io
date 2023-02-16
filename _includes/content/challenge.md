This workshop includes a data challenge, wherein we will release a large-scale dataset of images used by politicians, images shared by disinformation agents, and a sample of images shared in otherwise political contexts.
Using this dataset, we are soliciting solutions to address the following challenges:

1. Challenge 1: Identifying Influence Campaigns via Imagery While many efforts have worked to characterize influence campaigns (foreign or domestic, inauthentic and authentic), much of these efforts focus on text despite the multi-modal nature of these campaigns. Text is cheaper to produce and analyze, but images are more expensive and more engaging, making images both a potential vector for identifying coordinating accounts and key modality for measuring impact. This challenge asks for systems to use image-characterization methods to classify social media accounts into authentic or campaign accounts, where the campaign label is decomposed into sub-labels across several influence campaigns.

2. Challenge 2: Screenshot Sharing and Propagation As screenshots are increasingly used for reporting quotes and actions of elites across platforms, methods for tracking and attributing these screenshots to individuals are increasingly useful for establishing provenance and propagation paths. To this end, we must first understand how to separate screenshots of duplicate content. Systems submitted for this challenge will identify and cluster duplicate screenshots while being robust to cropping or resizing.


3. Challenge 3: Hate Symbols in News Images As producers of hate speech grow more sophisticated, images containing antisemitic and other racist symbols have successfully penetrated both social media and news coverage. How hate symbols are spread and potentially amplified by news outlets and social platforms has thus far been difficult to quantify given the complexity of image processing and the massive volume of visual media in online spaces. This challenge provides data from the ADL Hate Symbols Database (over 200 images as well as transformations produced using image augmentation algorithms) with the goal of developing classifiers to detect the likelihood that an image contains hate symbology. Questions center on whether hate symbols can be detected within larger visual datasets, such as protest coverage, and whether images can be rated on the probability of containing images that have recurrent characteristics of hate symbols.

4. Challenge 4: Antisocial Gestures in Presidential Debates The rise of populism and a contentious style of politics has placed a growing premium on displays of aggression in political debates. This is particularly true at the presidential level where candidates compete for viewer attention and political dominance. The antisocial gestures associated with aggression and contention on the debate stage are an important but often overlooked aspect of political behavior. This challenge provides C-SPAN videos and training set data (20% of each first presidential debate from 1980-2020 annotated at 10-second increments for a range of gestures and movements) with the goal of developing classifiers of the prevalence of antisocial gestures in televised debates. Questions include whether antisocial gestures align with aggressive facial expressions, voice tones, and language use, and whether these characteristics have increased or decreased over time.

### Data Challenge Posters

For those participating in the Data Challenge, we will ask they submit a challenge paper, which should contain the following elements:

- A description of the solution that you are proposing
- An evaluation of the solution
- A discussion of the implications of your solution and results

We highly encourage the source code of the solution to be included with the submission (e.g., in a GitHub repository), but this is not mandatory for acceptance of a data challenge paper.

The page limit for challenge papers is 4 pages (including all figures and tables) and unlimited references. 
All challenge papers will be reviewed by at least two program committee members. 
The best data challenge paper will be awarded by the track chairs and the program committee members.

Results of the data challenge will be shared at the workshop.

### Data Challenge Links

<!---
TODO: Add link to data repository
-->

Datasets for these challenges are available via this PhoMemes GitHub repository.

<!-- This dataset is organized into folders per account, so you get a sample of images per account.
In this folder, you will find:

#### Training Data

- `authenticity.training` - Samples of accounts and associated images across six classes, two authentic groups (`congress` from US Congresspeople and `political_images` from a sample of politically engaged US Twitter accounts) and four inauthentic groups.
- `screenshot.training` - Links to datasets that can be used for training to identify specific screenshots.

#### Challenge Data

- `challenge_data.large` - A large dataset of 2,095 accounts and about 21 images per account. 
- `challenge_data.small` - A small dataset of 411 accounts and about 21 images per account. This dataset is a subsample of the large dataset. -->

