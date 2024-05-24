## Description

This is a fork of https://github.com/hjwdzh/QuadriFlow with some changes:

1. Append generator of the static library for Linux OS and Windows OS.
2. Replace quit() method into an exception to catch error in the [pyQuadriflow](https://github.com/satabol/pyQuadriFlow) else Blender will quit on errors this library.

In Blender this remesher used in the Mesh->Remesh->Quad menu:

![image](https://github.com/satabol/QuadriFlow/assets/14288520/56dd4baf-284f-4cbb-b866-61b434e44b1b)

## Windows Build

There is **quadriflow.lib** has to be gotten at the end of this part.

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

