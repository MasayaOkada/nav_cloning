# nav_cloning

## install
* 環境 ubuntu18.04, ros melodic

* ワークスペースの用意
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
catkin_init_workspace
cd ../
catkin_make
```
* nav_cloningの用意
```
cd ~/catkin_ws/src
git clone https://github.com/MasayaOkada/nav_cloning.git
wstool up
wstool merge nav_cloning.install
wstool up
rosdep init
rosdep install
cd ../../
catkin_make
```
* その他インストール
```
pip install chainer==6.0
pip install scikit-image
```
