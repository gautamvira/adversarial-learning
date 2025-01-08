# adversarial-learning
## Adversarial Learning on the MNIST dataset using a Convolutional Neural Network
### Non-Targeted PGD Attack:
**Procedure** : 2 classifiers are trained using the parameters: (alpha: 0.02, 0.5), (perturbation radius: 0.3, 0.3), (steps: 20, 1).
In order to implement the PGD attack, first a tensor is created of the size of the input X; then the sum of X and a random value from the uniform distribution (-epsilon, epsilon) is given to the created tensor; this is the initial point. The model is used to make predictions using the perturbed input (tensor created) and the loss between the true labels and the predicted labels maximized by adding the signed gradients (* alpha) to the perturbed input (gradient ascent). The tensor is projected to the linf ball by clamping it between X-epsilon and X+epsilon. This process is repeated for every epoch.
### Targeted PGD attack:
**Procedure** : 1 classifier is trained using the parameters: (alpha: 0.02), (perturbation radius: 0.3), (steps: 20).
In order to implement this attack, a tensor for the perturbed input is created as mentioned above using the same initialization. However, instead of using the true labels to calculate the loss, a tensor is created with the largest element in the true labels; also, in the index in which the target label is equal to the true label, the target label is replaced with the second largest label. Upon computing the loss between the target labels and the predicted labels, the loss is minimized by performing gradient descent. The resulting perturbed input is projected to the linf ball as mentioned above.
