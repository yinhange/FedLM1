# 安装

torch==1.2

torchvision==0.4

ray == 1.0

# 使用

#### 目录结构

- glfl

  - log\ 

  - runs\ 

  - checkpoint\ 

  - main_test.py (主文件, cross-silo 模式)
  - main_dirichlet_selecyes_emnist.py (主文件， cross-device模式)

  - model.py (模型构建)

  - server.py (服务器对象定义)

  - utils.py 

  



#### 运行代码

```python
# cross-silo
python main_test.py --lr 0.03 --alg FedAvg --epoch 2000 --data_name CIFAR10 --extname hello --E 1

# cross-device
python main_dirichlet_selecyes_emnist.py --alg cdd_ci_plus --lr 0.03 --data_name CIFAR10 --alpha_value 0.01 --epoch 10000 --E 1
```

部分参数说明 :

--alg 算法选择，可选：

main_test.py:  < FedAvg, FedAvgM, SCAF, FedAdam, GLFL(IGFL-C), only-atte-self(IGFL-S) ,self-atte(IGFL) >

main_dirichlet_selecyes_emnist.py: < FedAvg, FedMoment, SCAF,  FedAdam, 

cdd_ci_plus(IGFL-C), only-atte-self(IGFL-S),  self-atte(IGFL) >



--data_name  数据集选择  可选 < CIFAR10, EMNIST>

--alpha_value 浓度值，控制Non-IID < 100, 0.1 0.01 >   （对应到论文里要乘10）

--E 一轮本地更新的epoch次数

