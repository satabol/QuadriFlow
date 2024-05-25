## Description

This is a fork of https://github.com/hjwdzh/QuadriFlow with some changes:

1. Append generator of the static library for Linux OS and Windows OS.
2. Replace quit() method into an exception to catch error in the [pyQuadriflow](https://github.com/satabol/pyQuadriFlow) else Blender will quit on errors this library.

In Blender this remesher used in the Mesh->Remesh->Quad menu:

![image](https://github.com/satabol/QuadriFlow/assets/14288520/56dd4baf-284f-4cbb-b866-61b434e44b1b)

As a result, two files are generated: 
- **quadriflow.lib** (for Windows)
- **libquadriflow.a** (for Linux)

## Windows Build

#### Dependencies

boost: https://www.boost.org/users/download/

![image](https://github.com/satabol/QuadriFlow/assets/14288520/be071aa3-2fca-47e2-9921-3be2c2b01d1a)

Remember boost folder: **E:\github.com\boost_1_85_0**

#### Clone quadriflow:
```
mkdir e:\github.com
cd /d e:\github.com\
git clone https://github.com/satabol/QuadriFlow.git
```

![image](https://github.com/satabol/QuadriFlow/assets/14288520/18d122eb-c197-4c07-a480-497cdf96b8fb)

```
cd QuadriFlow
mkdir build
cd build
```

![image](https://github.com/satabol/QuadriFlow/assets/14288520/5d5226f1-8e3e-45c1-bf8a-9d4974493049)

```
 cmake .. -DCMAKE_BUILD_TYPE=release -DBoost_INCLUDE_DIR=E:\github.com\boost_1_85_0
```

![image](https://github.com/satabol/QuadriFlow/assets/14288520/6fbb19dd-0890-4169-97a9-9f1e63488ef3)

Now you have Visual Studio 2022 Solution in the folder build:

![image](https://github.com/satabol/QuadriFlow/assets/14288520/034c8e1e-8733-4430-a46c-6326c6214b9b)

open this solution in the Visual Studio and build it. If all ok then you have to see static library **quadriflow.lib**. It will used later to build static library pyQuadriflow.

![image](https://github.com/satabol/QuadriFlow/assets/14288520/a36200d2-d81e-452b-ad0e-792c2a4286c9)


## Linux Build

For Linux build I will use [WSL](https://learn.microsoft.com/en-us/windows/wsl/install). But one can repeat this process on the Linux too.

#### Dependency

install cmake if you have no it: 

```
apt-get install cmake git
```

Create folder /opt/github.com and open teminal here. Now clone
- **quadriflow** (https://github.com/satabol/quadriflow.git)*
- **eigen** https://github.com/PX4/eigen
- **boost** https://www.boost.org/users/download/ (one can download it manually)

```
git clone https://github.com/satabol/quadriflow
git clone https://github.com/PX4/eigen
wget https://boostorg.jfrog.io/artifactory/main/release/1.85.0/source/boost_1_85_0.zip
unzip boost_1_85_0.zip .
```

![image](https://github.com/satabol/QuadriFlow/assets/14288520/b5451163-cab1-4e4f-b5a8-08b9408a6f2b)

open eigen, create 'build' folder, open it and build it:

```
cmake .. -DCMAKE_INSTALL_PREFIX:PATH=/opt/github.com/eigen/build
make -j install
```

Now you get eigen installed:

![image](https://github.com/satabol/QuadriFlow/assets/14288520/1e3f9d3a-4562-48ae-b458-76679c4ebf2c)


Now open quadriflow folder, make folder with name **build** and open it:

```
cmake .. -DCMAKE_BUILD_TYPE=release -DEIGEN_INCLUDE_DIR=/opt/github.com/eigen/build/include/eigen3/ -DBoost_INCLUDE_DIR=/opt/github.com/boost_1_85_0 -DCMAKE_CXX_FLAGS="-fpic"
make -j
```

![image](https://github.com/satabol/QuadriFlow/assets/14288520/253bab4b-512d-41a5-a16b-8e5fbb40c31d)

## Result

Now we have two static library files for pyQuadriFlow https://github.com/satabol/pyQuadriFlow:

![image](https://github.com/satabol/QuadriFlow/assets/14288520/755a6806-f8de-4767-9780-6a4a653d956b)