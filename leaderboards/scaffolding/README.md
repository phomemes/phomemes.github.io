# Scaffolding Code for PhoMemes Challenge

We provide scaffolding code as necessary to support engagement with the PhoMemes challenge. 
This scaffolding includes:

- `Scaffold-MapEmbeddingsToImageIDs.ipynb` -- Code to join embeddings gathered from each account in the training data to the corresponding image ID. This image ID corresponds to an image filename, which may be available in the [Raw Actor Images](https://drive.google.com/drive/folders/1q4qk1XHLiSNRjY9m1KKYxfs6DIy4SrDr?usp=share_link) dataset.

- `Scaffold-MapEmbeddingsToImageIDs-ClusterVisualization.ipynb` -- Building on the mapped embeddings-to-image-IDs, we use the full embedded dataset for all actors and apply k-means to it to identify clusters within the image data. Then, we test for which embeddings we have raw images and use those raw images to characterize each cluster and visualize them in a single-level treemap.