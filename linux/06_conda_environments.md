# **Conda Enviroments**

This is a multiple part series describing the use and deployment of `Virtual Environments`, `Virtual Machines`, and `Container` systems.

### **Why?**

In the age of Big Data, research is often shared with many people, repeated, and often scaled up depending on the size of the project. Therefore, the underlying algorithms, software and infrastructure must be `replicable` across many workstations, environments, servers, clusters, or even into the cloud. In order for research to be `replicable`, software developers often describe a set of instructions that define what is required by their algorithms/software to run correctly. These instructions often define other software that is required (**dependencies**), or even the operating system (Windows, Linux, OS X) that is needed to execute the analyses correctly and efficiently.

For example, when you install software into your Linux operating system, if you have `administrator` access to your workstation, you might download a package from the developer's website, then install the package according to their instructions. Often, you may need to tell your operating system where to find the newly installed package; this is usually done by adding the package's location to your `PATH` variable. Over time, after you have installed many software packages, your `PATH` variable might look like this:

![Path Variable](assets/06-01_path_variable.png)
*Image downloaded from:* [https://astrobiomike.github.io/bash/modifying_your_path](https://astrobiomike.github.io/bash/modifying_your_path)

This is a little hard to read, but the author provided another way to look at this `PATH` variable:

![Path Variable](assets/06-02_path_variable.png)
*Image modified from:* [https://astrobiomike.github.io/bash/modifying_your_path](https://astrobiomike.github.io/bash/modifying_your_path)

There are few things of interest to note in this example. First, he has two different versions of `Python` declared. Which version will be used by his Linux operating sytem? Second, what happens if he, for example, installs a new version of `MUMmer`? Would that require an updated version of `Python`? What if he installs a software package that requires `Python` version **2+** and not **3+**? 

There are some potential solutions to this problem, one of which would be to have different versions of his `.bashrc` or `.profile`, and then use the `source` command in Linux to load the environment and `PATH` variable that he requires for each project.

But what if there is an easier way?

### **How? (Part 1)**

There are multiple solutions to the problem described aboved, and the solution we will focus on in this section are `Virtual Environments`.

However, before going in to detail on `Virtual Environments`, let's take a step back and look broadly at some of the solutions.

### **What?**

We have previously set up a `Virtual Machine` to run `Xubuntu` alongside `Windows`, so how are they related to `Virtual Environments` and `Container Systems`?

From the smallest 'footprint' to the largest, at the most basic level:

* a `Virtual Environment` encapsulates a set of **software** instructions or **dependencies**
* a `Docker Container` or `Container System` encapsulates the entire **software environment**
* a `Virtual Machine` encapsulates an the **software environment**, its **Operating System** and the underlying **Hardware**

![Containers Versus Machines](assets/06-03_containers_versus_machines.png)

We will learn more about `Docker` in the next section, but briefly `Docker Containers` have major advantages over traditional `Virtual Machines`:

* they share hardware with the underlying server or workstation
* they can be scaled to use multiple processers very easily
* they are smaller (few MBs versus 10s or 100s of MBs)

In practice, we can use a package environment manager like `conda` inside of a `Docker Container` system, and then use the `Container` across multiple servers, workstations, or users very easily.

### **How? (Part 2)**

Let's return to `Virtual Environments`. As described above, `Virtual Environments` encapsulate a set of **software** instructions or **dependencies**. When we wish to install a new software package, that software often **depends** on existing software to run. For example, let's look at the software required by the latest version of `TensorFlow` to run on a Linux workstation:

| Name | Version |
|-----:|:--------|
| absl-py | 0.7.1 |
| astor | 0.7.1 |
| bzip2 | 1.0.6 |
| c-ares | 1.15.0 |
| ca-certificates | 2019.3.9 |
| certifi | 2019.3.9 |
| gast | 0.2.2 |
| grpcio | 1.16.0 |
| h5py | 2.9.0 |
| hdf5 | 1.10.4 |
| keras-applications | 1.0.7 |
| keras-preprocessing 1.0.9 |
| libblas | 3.8.0 |
| libcblas | 3.8.0 |
| libffi | 3.2.1 |
| libgcc-ng | 8.2.0 |
| libgfortran-ng 7.3.0 |
| liblapack | 3.8.0 |
| libprotobuf 3.7.1 |
| libstdcxx-ng 8.2.0 |
| markdown | 2.6.11 |
| mock | 3.0.5 |
| ncurses | 6.1 |
| numpy | 1.16.3 |
| openblas | 0.3.6 |
| openssl | 1.0.2r |
| pip | 19.1 |
| protobuf | 3.7.1 |
| python | 3.7.1 |
| readline | 7.0 |
| scipy | 1.2.1 |
| setuptools 41.0.1 |
| six | 1.12.0 |
| sqlite | 3.26.0 |
| tensorboard 1.13.1 |
| tensorflow 1.13.1 |
| tensorflow-estimator | 1.13.0 |
| termcolor | 1.1.0 |
| tk | 8.6.9 |
| werkzeug | 0.15.2 |
| wheel | 0.33.1 |
| xz | 5.2.4 |
| zlib | 1.2.11 |



# Name                    Version                   Build  Channel
_r-mutex                  1.0.0               anacondar_1  
bzip2                     1.0.6             h14c3975_1002    conda-forge
ca-certificates           2019.3.9             hecc5488_0    conda-forge
cairo                     1.14.6                        4    conda-forge
certifi                   2019.3.9                 py36_0    conda-forge
curl                      7.52.1                        0    conda-forge
fontconfig                2.12.1                        6    conda-forge
freetype                  2.7                           1    conda-forge
gatk                      3.8                           7    bioconda
gettext                   0.19.8.1          hc5be6a0_1002    conda-forge
glib                      2.51.4                        0    conda-forge
graphite2                 1.3.13            hf484d3e_1000    conda-forge
gsl                       2.4               h294904e_1006    conda-forge
harfbuzz                  1.4.3                         0    conda-forge
icu                       58.2              hf484d3e_1000    conda-forge
jpeg                      9c                h14c3975_1001    conda-forge
libblas                   3.8.0                8_openblas    conda-forge
libcblas                  3.8.0                8_openblas    conda-forge
libffi                    3.2.1             he1b5a44_1006    conda-forge
libgcc                    7.2.0                h69d50b8_2    conda-forge
libgcc-ng                 8.2.0                hdf63c60_1  
libgfortran-ng            7.3.0                hdf63c60_0  
libiconv                  1.15              h516909a_1005    conda-forge
libpng                    1.6.28                        1    conda-forge
libstdcxx-ng              8.2.0                hdf63c60_1  
libtiff                   4.0.7                         0    conda-forge
libxml2                   2.9.5                         0    conda-forge
ncurses                   5.9                          10    conda-forge
openblas                  0.3.6                h6e990d7_1    conda-forge
openjdk                   8.0.192           h14c3975_1003    conda-forge
openssl                   1.0.2r               h14c3975_0    conda-forge
pango                     1.40.4                        0    conda-forge
pcre                      8.41              hf484d3e_1003    conda-forge
pip                       19.1                     py36_0    conda-forge
pixman                    0.34.0            h14c3975_1003    conda-forge
python                    3.6.3                         0    conda-forge
r-assertthat              0.2.0                  r3.3.2_0    conda-forge
r-base                    3.3.2                         5    conda-forge
r-bitops                  1.0_6                  r3.3.2_0    conda-forge
r-catools                 1.17.1                 r3.3.2_1    bioconda
r-colorspace              1.3_2                  r3.3.2_0    conda-forge
r-dichromat               2.0_0                  r3.3.2_0    conda-forge
r-digest                  0.6.12                 r3.3.2_0    bioconda
r-gdata                   2.18.0                 r3.3.2_0    conda-forge
r-ggplot2                 2.2.1                  r3.3.2_0    bioconda
r-gplots                  2.17.0                 r3.3.2_0    bioconda
r-gsalib                  2.1                    r3.3.2_0    bioconda
r-gtable                  0.2.0                  r3.3.2_0    conda-forge
r-gtools                  3.5.0                  r3.3.2_0    conda-forge
r-kernsmooth              2.23_15                r3.3.2_0    conda-forge
r-labeling                0.3                    r3.3.2_0    conda-forge
r-lazyeval                0.2.1                  r3.3.2_0    conda-forge
r-magrittr                1.5                    r3.3.2_0    conda-forge
r-mass                    7.3_48                 r3.3.2_0    conda-forge
r-munsell                 0.4.3                  r3.3.2_0    conda-forge
r-plyr                    1.8.4                  r3.3.2_0    conda-forge
r-rcolorbrewer            1.1_2                  r3.3.2_0    conda-forge
r-rcpp                    0.12.16                r3.3.2_0    conda-forge
r-reshape                 0.8.6                  r3.3.2_0    bioconda
r-reshape2                1.4.3                  r3.3.2_0    conda-forge
r-scales                  0.4.1                  r3.3.2_1    bioconda
r-stringi                 1.1.7                  r3.3.2_1    conda-forge
r-stringr                 1.2.0                  r3.3.2_0    conda-forge
r-tibble                  1.2                    r3.3.2_1    bioconda
readline                  6.2                           0    conda-forge
setuptools                41.0.1                   py36_0    conda-forge
sqlite                    3.13.0                        1    conda-forge
tk                        8.5.19                        2    conda-forge
wheel                     0.33.1                   py36_0    conda-forge
xz                        5.2.4             h14c3975_1001    conda-forge
zlib                      1.2.8                         3    conda-forge
