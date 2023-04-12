# Barlow Twins
## J. Zbontar, 2021, "Barlow Twins: Self-Supervised Learning via Redundancy Reduction"

This paper proposes an objective function that naturally avoids such collapse by measuring the cross-correlation matrix between the outputs of two identical networks fed with distorted versions of a sample, and making it as close to the identity matrix as possible. This causes the representation vectors of distorted versions of a sample to be similar, while minimizing the redundancy between the components of these vectors.

This does not require large batches, nor does it require any asymmetric momentum encoders or stop-gradients. Intriguingly, Barlow Twins (BT) strongly benefits from the use of very high-dimensional representations.

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img1.daumcdn.png?raw=true)

BT distinguishes itself from other methods by its innovative loss function LBT:

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img2.daumcdn.png?raw=true)

where λ is a positive constant trading off the importance of the first and second terms of the loss, and C

is the cross-correlation matrix computed between the outputs of the two identical networks along the batch dimension:

C=(Z^A)^T*Z^B

Z^A∈R^N×D
and Z^B∈R^N×D

are two different views of the original view, and they are assumed to be mean-centered with its standard deviation of 1 along the batch dimension.

Intuitively, the invariance term of the objective makes the representation invariant to the distortions applied. The redundancy reduction term decorrelates the different vector components of the representation.

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img3.daumcdn.png?raw=true)

Architecture: The encoder consists of a ResNet-50, followed by a projector network. The projector network has three linear layers, each with 8192 output units. The first two layers of the projector are followed by a batch normalization layer and ReLU.

Optimization: Batch size: 2048 (Yet, it even works well with batches as small as 256); λ

: 5e-3; Weight decay: 1.5e-6.
Results


![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img4.daumcdn.png?raw=true)

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img5.daumcdn.png?raw=true)

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img6.daumcdn.png?raw=true)

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img7.daumcdn.png?raw=true)

(Left) 'Normalization along feature dim.' refers to the common l2-norm practice along with the feature dim. (Right) BT is robust w.r.t batch size while SimCLR requires a large batch size to obtain a lot of negative samples.

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img8.daumcdn.png?raw=true)

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img9.daumcdn.png?raw=true)

(Left) BT's performance increases with the projector's dimension size. (Right) BT doesn't really need 'stop-gradient' or 'predictor' at all.
