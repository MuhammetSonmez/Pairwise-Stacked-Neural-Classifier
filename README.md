# Pairwise Stacked Neural Classifier (PSNC)

**Pairwise Stacked Neural Classifier (PSNC)** is a custom stacking architecture developed for multi-class classification tasks, designed to achieve high accuracy even with limited data.

By combining the classical One-vs-One (OvO) approach with artificial neural networks (ANNs), the model introduces a meta-learning mechanism capable of capturing non-linear decision boundaries from prediction scores.

This model was designed during the development of my undergraduate thesis and has demonstrated successful experimental results. It is shared as open-source within the scope of this work.

## Features

* High classification accuracy with limited data
* A dedicated binary neural network for each class pair (based on OvO principle)
* Meta-learner: Learns to determine the final class label based on the outputs of the base models
* Learning-based decision mechanism instead of classical majority voting
* Capable of capturing complex, non-linear patterns between classes
* Easily integrable with transfer learning architectures (e.g., BERT)

## Model Architecture

![PNSC](https://github.com/user-attachments/assets/5b94f37e-ec38-4314-9929-597d9e269bd2)



## Usage Steps

1. Convert textual data into fixed-size embeddings using a transformer-based encoder such as BERT.
2. Train individual binary neural classifiers for each class pair (nC2 combinations).
3. Freeze these binary classifiers and use them solely for inference.
4. Represent each input sample as a vector of scores obtained from all pairwise classifiers.
5. Train a new neural network (meta model) that takes these score vectors as input and predicts the final class.
6. Use this pipeline for final inference on unseen samples.

## Academic Contribution

This architecture proposes a learning-based alternative to majority voting used in traditional OvO schemes.
By analyzing the decision patterns formed by the base models, the meta-learner provides improved classification accuracy, particularly in tasks requiring the learning of non-linear relationships.

The model has shown to be effective in tasks such as opinionated text classification, low-resource learning, and imbalanced multi-class datasets.

## License

This work is licensed under the Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) license.

Commercial use of this model or its architectural components requires explicit permission from the author. Please contact for licensing inquiries.
