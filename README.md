The classification of handwritten digits is a fundamental problem in the field of machine learning, often used as a
benchmark for comparing different models and techniques. In this project, we tackle the problem of classifying
digits from the MNIST dataset using deep neural networks. The MNIST dataset is a widely recognized benchmark
dataset that contains 70,000 images of handwritten digits, each labeled from 0 to 9. The objective is to train models
that can accurately predict the digit represented in each image.
For this task, two different neural network architectures are explored: a fully connected Multi-Layer Perceptron
(MLP) and a Convolutional Neural Network (CNN). The goal is to compare their performance in terms of
classification accuracy, training efficiency, and generalization to unseen data. The MLP model serves as a baseline,
while the CNN leverages the spatial structure of the images to enhance performance.
Through experimentation, we aim to evaluate how these models handle the digit classification task, comparing their
training and validation accuracy, and analyzing the hyperparameters that contribute to their success.
Methodology



In this project, two deep learning architectures were implemented and evaluated: a fully connected Multi-Layer
Perceptron (MLP) and a Convolutional Neural Network (CNN). The following subsections detail the design,
training, and hyperparameter tuning for each model.
Data Preprocessing :The MNIST dataset consists of 28x28 pixel grayscale images of handwritten digits, along with
their corresponding labels (0-9). To prepare the data for training:
Normalization: The pixel values were normalized to the range [0, 1] by dividing by 255.
Train-Test Split: The dataset was split into 60,000 training images and 10,000 test images.
Batching: The data was loaded into batches of size 64 for training and testing.




2. Multi-Layer Perceptron (MLP)
The first architecture implemented was a fully connected neural network, also I implemented another model to
compare with MLP. This model serves as a baseline to compare with the CNN.
Architecture:
Input Layer: 784 units (28x28 flattened input image).
Hidden Layer 1: 128 units, ReLU activation.
Hidden Layer 2: 64 units, ReLU activation.
Output Layer: 10 units (one for each digit), Softmax activation.
Training Process: Loss Function: Cross-Entropy Loss.
Optimizer: Adam optimizer with a learning rate of 0.001.
Epochs: The model was trained for 10 epochs.
Batch Size: 64 samples per batch.
Validation: The model’s performance was validated after each epoch on the test set.
Results: After 10 epochs, the MLP achieved a test accuracy of 95.17%. The loss steadily decreased, but the MLP
struggled with complex patterns that require spatial relationships in the data.




3. Convolutional Neural Network (CNN)
The second model was a CNN, which leverages the spatial structure of the images for better feature extraction.
CNNs are known to outperform MLPs in image-based tasks due to their ability to detect patterns like edges, shapes,
and textures.
Architecture:
Convolutional Layer 1: 16 filters, 3x3 kernel, ReLU activation, followed by Max Pooling (2x2).
Convolutional Layer 2: 32 filters, 3x3 kernel, ReLU activation, followed by Max Pooling (2x2).
Fully Connected Layer 1: 128 units, ReLU activation.
Fully Connected Layer 2: 10 units, Softmax activation.
Training Process: Loss Function: Cross-Entropy Loss.
Optimizer: Adam optimizer with a learning rate of 0.001.
Epochs: The model was trained for 10 epochs.
Batch Size: 64 samples per batch.
Dropout: Dropout regularization with a probability of 0.5 was applied to the fully connected layers to prevent
overfitting.
Results:
The CNN achieved a test accuracy of 99.35% after 10 epochs.
The model was able to capture spatial hierarchies in the data, significantly outperforming the MLP.

4. Hyperparameter Tuning
Hyperparameter tuning was applied to improve the model’s performance. The following hyperparameters were
tuned:
Learning Rate: Initial experiments were conducted with a learning rate of 0.01, which was later reduced to 0.001 for
more stable convergence.
Dropout: Dropout was applied to the fully connected layers in the CNN with a probability of 0.5 to reduce
overfitting.
Activation Functions: ReLU activation was used in both models due to its efficiency in handling vanishing gradient
problems.
The combination of these hyperparameters allowed the CNN to generalize better to unseen data.
Empirical Results and Evaluation: Detailed Analysis
Performance Overview with Initial Simple CNN Model :
- Training: The CNN model quickly converged, achieving an accuracy of **99.35%** on the test set.
- Test Set Performance: Average Loss: 0.0009 / Accuracy: 98.86% (9886/10000)
Training Loss: The loss decreased rapidly, from 0.1429 in Epoch 1 to 0.0049 in Epoch 10.
Training Accuracy: The model achieved an accuracy of 99.86% on the training set and 98.86% on the test set.
- MLP Model:
- Training: Achieved a final accuracy of 97.31% after 10 epochs.
- MLP Model with Dropout and Hyperparameter Tuning
- Training: The modified MLP showed improved stability but slightly lower accuracy of 95.17%.
- Improved CNN Model with Dropout :
- Test Set Accuracy: 99.35%
- Precision, Recall, and F1-Scores: The CNN consistently achieved high precision, recall, and F1 scores across all
digits, ranging from 0.99 to 1.0
-Highest performance was observed for digit classes 1, 2, 8, and 9.
Impact of Dropout on CNN Model Incorporating dropout in the CNN model improved generalization, reducing
overfitting without compromising accuracy
Training Loss: The loss decreased steadily from 0.2504 in Epoch 1 to 0.0186 in Epoch 10.
Test Accuracy: The test accuracy improved to 99.35%, surpassing both the MLP and the initial CNN model.
- Dropout Rate : Applied a dropout rate of 0.5 after fully connected layers. This led to improved robustness and
ensured that the model didn't memorize the training data.
- Accuracy: Despite the randomness introduced by dropout, accuracy remained consistently high at 99.35% , a
notable improvement compared to the initial model without dropout.
- Effect of Dropout : Dropout improved the generalization by regularizing the network. With overfitting being
controlled, the CNN model generalized better to unseen data, which is evident from its performance on the test set.
Detailed Metrics for CNN Model
- Classification Report : - Precision : Near perfect for all digits, ranging from 0.9884 to 0.9991 , indicating very few
false positives. the model achieved a precision of over 99% for all classes.
Recall: Similarly, the recall was above 99% for most classes, with class 5 showing a slight dip to 98.77%.Also near
perfect, reflecting the model's ability to correctly classify almost all true instances of each digit.
- F1-Score : he F1-score was consistently high across all classes, indicating a balanced performance in terms of
precision and recall. Maintained high scores across all digits, balancing precision and recall.
Per-Class Accuracy
- The CNN model performed exceptionally well on digits 1, 3, and 8 , with accuracies above 99.8%
- Even the least accurate classes, like 6 and 5, still had near-perfect accuracy, showing the CNN’s effectiveness
across the board.
Misclassified Examples
The misclassification rate was low, but the few errors occurred in digits that share visual similarities (e.g., 5 and 6).
These errors likely arose from certain images having ambiguous or distorted strokes.
Visualizing Activation Maps. The CNN’s activation maps helped understand what features the network focused
on. The early convolutional layers detected basic patterns, like edges and textures, while the deeper layers identified
more complex features, such as specific digit shapes. This feature hierarchy contributed to the high accuracy.
Comparison Between CNN and MLP
Accuracy: - MLP: Achieved an accuracy of **97.31%** with basic tuning.
- CNN: Significantly outperformed the MLP with an accuracy of **99.35%**.
Learning Capabilities: - MLP: Suitable for simpler tasks but struggled to capture spatial hierarchies in images,
leading to slightly worse performance.
- CNN : Leveraged its convolutional layers to extract meaningful spatial patterns, which improved its classification
ability for image data.
- Generalization: - MLP: The addition of dropout improved generalization, but the model's capacity was still
limited due to its fully connected architecture.
- CNN: Dropout further improved the generalization of the CNN, and the combination of convolutional and pooling
layers allowed the model to achieve better robustness on unseen data.



Observations:
ReLU activation played a crucial role in mitigating the vanishing gradient problem, allowing the network to learn
deeper features effectively.
Loss Reduction: The loss during training for the CNN dropped much more rapidly than the MLP, especially in the
early epochs. This indicates that the CNN model is much more efficient at learning from the image data, likely due
to the convolutional layers capturing spatial hierarchies and patterns.
Accuracy: The CNN outperformed the MLP by a significant margin, achieving an accuracy of 99.35% on the test
set. The model's ability to generalize well to unseen data suggests that CNNs are much more effective for image-
based tasks like digit classification.
Class-wise Performance: The CNN achieved near-perfect accuracy for most classes, with some classes (like digits
3 and 8) having slight dips in performance. However, these differences are negligible given the overall strong
performance across all classes.
Multi-Layer Perceptron (MLP) Results
The MLP model was trained for 10 epochs and produced the following key results:
Training Accuracy: 97.31%
Test Accuracy: 95.17%


Conclusion The CNN model outperformed the MLP in both training and test performance, especially after
incorporating dropout to prevent overfitting. The CNN demonstrated superior generalization, higher accuracy, and
better learning of spatial hierarchies. The final accuracy of 99.35% and high precision/recall metrics for all classes
provide solid evidence that CNN is the best model for the MNIST classification task in this project.
Lessons Learned



1. Importance of Network Architecture: The project highlighted how choosing the right architecture (MLP vs.
CNN) significantly impacts performance. Convolutional Neural Networks (CNNs) are far more effective in image
classification tasks compared to basic Multi-Layer Perceptrons (MLPs) due to their ability to extract spatial features.
2. Effectiveness of Dropout: Introducing dropout helped regularize the models by preventing overfitting,
particularly in the CNN. This enhanced the model's ability to generalize to unseen data, ensuring that it did not just
memorize the training dataset.
3. Model Optimization: Hyperparameter tuning (learning rate, dropout, optimizer choice) was crucial for
improving the performance. Lower learning rates helped achieve smoother convergence, while using the Adam
optimizer sped up training and stabilized performance.
4. Metrics Matter: Understanding precision, recall, and F1-scores helped identify areas of improvement in the
models. Even with high overall accuracy, misclassifications were analyzed using these metrics to find patterns in the
errors.



Problems Faced
1. Overfitting in Early Models: The initial CNN model without dropout tended to overfit the training data,
resulting in poorer performance on the test set. This issue was resolved by applying dropout, leading to improved
generalization.
2. MLP Limitations : The MLP model struggled to achieve high accuracy because it lacked the ability to
effectively capture spatial features in the MNIST dataset. This showed the limitations of fully connected layers for
image data.
3. Training Instability: During hyperparameter tuning, high learning rates caused unstable training behavior,
leading to either slow convergence or divergence. Fine-tuning the learning rate and optimizer helped stabilize the
training process.
4. Difficulty in Misclassification Analysis : Identifying why the model misclassified certain digits (like 5 and 6)
was challenging, as these errors often arose from subtle similarities or distortions in the digits. This highlighted the
limitations of even advanced models when dealing with ambiguous data.
How Libraries Helped
1. PyTorch: PyTorch provided a flexible and efficient platform for building and training both the MLP and CNN
models. Its dynamic computation graph allowed for easy experimentation with different architectures and
hyperparameters, and its powerful `DataLoader` API made data preprocessing straightforward.
2. Matplotlib & Seaborn: These libraries were invaluable for visualizing the results, including accuracy trends, loss
curves, and confusion matrices. They helped to easily interpret the training process and evaluate the models’
performance.
3. Scikit-learn: The `classification_report` and `confusion_matrix` functions from Scikit-learn provided detailed
performance metrics, making it easy to evaluate precision, recall, F1-score, and per-class accuracy, leading to a
deeper understanding of where the model succeeded or struggled.
4. Torchvision: Provided convenient access to the MNIST dataset and simplified data transformations, making it
easy to load, preprocess, and visualize the dataset during model exploration.



Conclusion
The primary goal of this project was to classify handwritten digits from the MNIST dataset using machine learning
techniques, specifically by comparing the performance of a simple Multi-Layer Perceptron (MLP) model and a
Convolutional Neural Network (CNN). Through careful experimentation and analysis, we successfully achieved this
goal by developing, training, and evaluating both models.
MLP Model: While the MLP model achieved a respectable accuracy of 97.31%, it struggled to capture the spatial
patterns in the data, which are crucial for image classification tasks. This limitation highlighted the need for a more
sophisticated model, like CNNs, which are designed to handle image data more effectively.



CNN Model: The CNN model outperformed the MLP by a significant margin, reaching an accuracy of 99.35%. This
result confirms the superiority of CNNs in recognizing spatial hierarchies and extracting features from images. The
introduction of dropout layers played a vital role in preventing overfitting and improving generalization, as seen in
the model's high test accuracy. The classification report for the CNN model also demonstrated high precision, recall,
and F1-scores across all digit classes, further proving its robustness.
Hyperparameter Tuning: Careful tuning of learning rates, dropout rates, and the optimizer (Adam) improved the
performance of both models, with the CNN benefitting the most. The CNN's ability to maintain high accuracy across
all digit classes further reinforces its reliability and robustness in classification tasks.




In conclusion, successfully met the project’s goals of developing, training, and evaluating models for digit
classification. The CNN emerged as the best-performing model due to its ability to effectively capture spatial
features, achieve high accuracy, and generalize well to unseen data. This project demonstrates the importance of
model architecture selection, regularization techniques like dropout, and detailed evaluation in achieving top
performance in machine learning tasks.
