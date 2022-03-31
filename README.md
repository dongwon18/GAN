---
finished_date: 2021-11-11
tags:
  - PyTorch
  - GAN
  - MNIST
---
# GAN
build and train basic GAN model with MNIST dataset using PyTorch
- GAN has two parts: generator and discriminator.
- Generator tries to cheat discriminator by creating new data from given data.
- Discriminator tries to find out which data is fake given by generator.
- Two parts compete

## Parameters
- batch size: 128
- image size: 28 * 28
- epoch: 200

## Generator
- set noise, hidden referencing given code(Week10_01_GAN_1104.ipynb)
- size: size of input, final output of generator will size * size
    - (for MNIST, 28 * 28)
- a: slope gradient for LeakyReLU, default = 0.01
- droprate: droprate for Dropout, default = 0.1(referencing given code) 
- noise -> hidden -> hidden -> input size -> (tanh)
- use LeakyReLU to avoid gradient vanishing problem
---
- try to make output becomes 1(1 means real)
    - since generator make fake image and want to cheat discriminator
- on the other hand, discriminator tries to make output becomes 0(0 means fake)
    - since discriminator want to find out that the input is fake

## Discriminator
- hidden, size, a, droprate are also set as default
- input size -> hidden -> hidden -> 1 -> (sigmoid)
- use BCELoss as loss function, need sigmoid

## Result
- Generator loss: 1.50
- Discriminator loss: 0.98
- can see result as image in ipynb file.

## 배운 점
- GAN에서는 generator, discriminator가 경쟁한다. (적대적 학습법)
- generator는 discriminator를 속이기 위해 학습한 데이터를 바탕으로 가까 데이터를 만들어낸다.
- discriminator는 generator가 생성산 데이터 중 어떤 것이 진짜이고 어떤 것이 가짜인지 알아낸다.
- generator는 discriminator의 결과값을 바탕으로 학습한다. 반면 discriminator는 generator의 결과값을 바탕으로 학습한다.
- GAN을 이용하여 새로운 이미지를 생성하거나 복원할 수 있다.

## 한계점
- MNIST 데이터 외에 원 논문에서 사용했던 TFD, CIFAR-10 등 다른 데이터에도 적용시켜 보는 것이 좋을 듯하다.
