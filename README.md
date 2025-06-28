作用：平面图的识别，可以识别门框和墙体

原理：通过对图片进行二值处理，筛选出高于某些黑度阈值的像素。因为在平面图中墙体的颜色大部分都是深灰色/黑色，高于普通结构的值，所以能够提取出来。另外还进行了一些噪声处理和连通性补全，可以消除一些噪点，以及补全缝隙。

限制：不同图片的二值化情况不一样，需要人肉眼去调整阈值，才能够达到最优的情况

运行环境：jdk11

运行步骤：按照下面提供的命令运行即可，需要注意的是由于网络环境问题可能下载依赖会失败，可以通过给命令行设置代理解决；另外需要修改 `build.gradle` 文件增加国内镜像源。

```
repositories {
    maven { url 'https://maven.aliyun.com/repository/public' } 
    maven { url 'https://maven.aliyun.com/repository/google' }
    mavenCentral()
    jcenter()
}
```


# Automatic analysis and simplification of architectural floor plans [![Build Status](https://travis-ci.org/cansik/architectural-floor-plan.svg?branch=master)](https://travis-ci.org/cansik/architectural-floor-plan) [![codebeat badge](https://codebeat.co/badges/244f2179-f84e-4a39-8943-3285d0cf8337)](https://codebeat.co/projects/github-com-cansik-architectural-floor-plan) [![DOI](https://zenodo.org/badge/69436030.svg)](https://zenodo.org/badge/latestdoi/69436030)
This software is an architectural floor plan analysis and recognition system to create extended plans for building services.

## Abstract
The goal of this work is to do a fast and robust room detection on floor plans. The idea is, that a wide range of non standardized floor plans can be analyzed, time efficient, with little drawbacks in its precision.
The used workflow consists of several algorithms, that are combined to deliver the expected result. It consists of *Morphological cleaning* for noise removal, *Machine Learning* and *Convex Hull closing* for gap closing and a *Connected Component analysis* for the final room detection. It is the best result out of different approaches that were tested. All of the algorithms used, use an image of a plan  as the start for detection and return the location and size of each room as a CSV-table or SVG-vectors. The software is prepared to return the rooms as a DWG- or DXF-Format for a CAD-Program, but the license for a library, to convert the format, is not finally evaluated. The algorithm implemented, shows improvement in room detection accuracy, compared to similar works done in the last few years.

![Afpars](readme/afpars.jpg)

## Run the application
The software is still a prototype and not packaged into an executable. To run the software, you have to run the following command:

```bash
cd afpars

# unix / macOS
./gradlew run

# windows
gradlew.bat run
```

## Development prerequisites
For development on the existing project, you have to install a modern Java Development Kit (`>=11`). OpenJDK is supported!

The project itself can be built with the [gradle build tool](https://gradle.org/).

```bash
cd afpars

# unix / macOS
./gradlew build

# windows
gradlew.bat build
```


## About
*FHNW Bachelor Computer Science*

*Alexander Wyss and Florian Bruggisser*
