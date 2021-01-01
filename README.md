# ubuntu_setting
ubuntu16.04 setting

* k380 키보드 fn키 lock 걸기
dmesg | grep hidraw
https://github.com/jergusg/k380-function-keys-conf

* 테스크탑 UI 변경
sudo apt-get install xfce4
sudo apt-get install xubuntu-default-settings

* gpu 정보 받아오기 위해 nvidia 드라이버 설치
https://devyurim.github.io/development%20environment/ubuntu/2018/05/24/ubuntu-2.html

$ sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
$ sudo sh -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64 /" >> /etc/apt/sources.list.d/cuda.list'
$ sudo sh -c 'echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64 /" >> /etc/apt/sources.list.d/cuda.list'
$ sudo apt-get update

apt-cache search nvidia
sudo apt-get install nvidia-384

command line을 이용한 설치 이외에 다른 방법으로는
sofrware & update 에서 Additional Drivers 탭을 선택하면 설치 가능한 nvidia 드라이버들이 나열되어있다.  
선택하여 Apply Changes를 해줘도 된다.

* python 날려서 UI 안 되었을 때 복구했던 방법
https://askubuntu.com/questions/218919/i-accidentally-deleted-usr-bin-python-how-do-i-restore-it
