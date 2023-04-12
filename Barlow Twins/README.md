# Barlow Twins
## J. Zbontar, 2021, "Barlow Twins: Self-Supervised Learning via Redundancy Reduction"

This paper proposes an objective function that naturally avoids such collapse by measuring the cross-correlation matrix between the outputs of two identical networks fed with distorted versions of a sample, and making it as close to the identity matrix as possible. This causes the representation vectors of distorted versions of a sample to be similar, while minimizing the redundancy between the components of these vectors.

This does not require large batches, nor does it require any asymmetric momentum encoders or stop-gradients. Intriguingly, Barlow Twins (BT) strongly benefits from the use of very high-dimensional representations.

![alt text](https://github.com/ajmal001786/Paper-review/blob/main/Barlow%20Twins/pics/img1.daumcdn.png?raw=true)
