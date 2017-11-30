# Set up for Schwartz Lab Basic Droplet

## Installed Programs

### Program: Java; Version: Java8-OpenJDK
##### Installation Commands:
```
sudo apt-get install default-jre
sudo apt-get install default-jdk
```
---
### Program: Anaconda; Version: 5.0.1 (For Python v3.6)
##### Notes: Installed into /opt/anaconda3/
##### Installation Commands:
```
wget https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh
sh Anaconda3-5.0.1-Linux-x86_64.sh
conda create -n py363 python=3.6.3 anaconda
conda create -n py2714 python=2.7.14 anaconda

#To activate/deactivate Python v.3.6.3 - source activate py363
#To activate/deactivate Python v.2.7.14 - source activate py2714
#To deactivate current Python environment - source deactivate
```
---
### Program: R; Version: 3.4.2

##### Installation Commands:
```
sudo sh -c 'echo "deb http://cran.rstudio.com/bin/linux/ubuntu xenial/" >> /etc/apt/sources.list'
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
sudo apt-get update
sudo apt-get install r-base
```
##### Note: Added 1G of Swap (per https://deanattali.com/2015/05/09/setup-rstudio-shiny-server-digital-ocean/)
```
sudo /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
sudo /sbin/mkswap /var/swap.1
sudo /sbin/swapon /var/swap.1
sudo sh -c 'echo "/var/swap.1 swap swap defaults 0 0 " >> /etc/fstab'
```
---
### Program: R-Studio; Version: 1.1.383
##### Installation Commands:
```
sudo apt-get -y install libapparmor1 gdebi-core
wget https://download2.rstudio.org/rstudio-server-1.1.383-amd64.deb
sudo gdebi rstudio-server-1.1.383-amd64.deb
```
---
### Program: shiny-server; Version: 1.5.5.872
##### Installation Commands:
```
wget https://download3.rstudio.org/ubuntu-12.04/x86_64/shiny-server-1.5.5.872-amd64.deb
sudo gdebi shiny-server-1.5.5.872-amd64.deb
```
---
### Program: GNU Parallel
```
sudo apt-get install parallel
```
---
### Program: cmake
```
sudo apt-get install cmake
```
---
### Program: gcc; Version: 6.3.0
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install gcc-6
sudo apt-get install g++-6
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6
```
---
### Program: mpich; Version: 3.2
```
sudo apt-get install mpich
```
---
### Program: samtools; Version: 1.3.1 (For SISRS)
```
wget https://downloads.sourceforge.net/project/samtools/samtools/1.3.1/samtools-1.3.1.tar.bz2
tar -xjvf samtools-1.3.1.tar.bz2
mv samtools-1.3.1 /opt
./configure --prefix=/opt/samtools-1.3.1/SISRS
make && make install
#Added /opt/samtools-1.3.1/SISRS/bin to /root/.bashrc PATH, comment out for samtools v.1.6
```
---
### Program: BBMap; Version: 37.68
```
wget https://downloads.sourceforge.net/project/bbmap/BBMap_37.68.tar.gz
tar -xvzf BBMap_37.68.tar.gz
mv bbmap /opt
#Added /opt/bbmap to /root/.bashrc PATH
```
---
### Program: SRAToolkit; Version: 2.8.2
```
wget --output-document sratoolkit.tar.gz http://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz
tar -xzvf sratoolkit.tar.gz
mv sratoolkit.2.8.2-1-ubuntu64/ /opt/
#Added /opt/sratoolkit.2.8.2-1-ubuntu64/bin to /root/.bashrc PATH
```
---
### Program: Minia; Version: 2.0.7
```
wget https://github.com/GATB/minia/releases/download/v2.0.7/minia-v2.0.7-Source.tar.gz
tar -xzvf minia-v2.0.7-Source.tar.gz
mv minia-v2.0.7-Source/ /opt
mkdir build
cd build
cmake ..
make -j 4 && make install
#Added /opt/minia-v2.0.7-Source/build/bin to /root/.bashrc PATH
```
---
### Conda Installations
##### Bowtie2; Version: 2.3.0
##### Samtools; Version: 1.6.0
##### Mafft; Version: 7.310-0
##### Velvet; Version: 1.2.10-1
##### AbySS; Version: 2.0.1-boost1.60-1
##### BioPython; Version: 1.69
##### PySAM; Version: 0.13.0
##### Trinity; Version: 2.4.0-5
##### BioPerl; Version: 1.6.924-4
##### ete3; Version: 3.1.1
##### Muscle; Version 3.8.1551
##### RAxML; Version: 8.2.10
##### Fasttree; Version: 2.1.10
##### BAMTools; Version: 2.4.1
##### NCBI BLAST; Version: 2.6.0

```
conda install -c bioconda bowtie2
conda install -c bioconda samtools
conda install -c bioconda mafft
conda install -c bioconda velvet
conda install -c bioconda abyss
conda install -c bioconda biopython
conda install -c bioconda pysam
conda install -c bioconda trinity
conda install -c bioconda perl-bioperl
conda install -c etetoolkit ete3
conda install -c bioconda muscle
conda install -c bioconda raxml
conda install -c bioconda fasttree
conda install -c bioconda bamtools
conda install -c bioconda blast
```
##### Note: Installed for both python environments
---
### Git Clones:

##### PhyML (11/30/2017; Version: 3.3.20170530)
```
git clone https://github.com/stephaneguindon/phyml.git
cd phyml/
./configure --enable-mpi --enable-phyml
make && make install
```
##### Ray (11/30/2017; Version: )
```
git clone https://github.com/sebhtml/ray.git
git clone https://github.com/sebhtml/RayPlatform.git
cd ray
make PREFIX=ray-build LDFLAGS="-lpthread" && make install
#Added /opt/GitClones/ray/ray-build to /root/.bashrc PATH
```
##### SISRS (11/30/2017; RAL Version)
```
git clone https://github.com/BobLiterman/SISRS.git
cd SISRS
#Added /opt/GitClones/SISRS/bin to /root/.bashrc PATH
```
---
### R-Packages:
- devtools
- daattali/shinyjs
- shiny
---
### Libraries Added:
```
sudo apt-get -y install libcurl4-gnutls-dev
sudo apt-get -y install libxml2-dev
sudo apt-get -y install libssl-dev
```
