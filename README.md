## 기본 세팅  
https://github.com/rcasero/doc/wiki/Ubuntu-linux-on-Dell-XPS-15-(9560)#touchpad  

## k380 키보드 fn키 lock 걸기  
https://github.com/jergusg/k380-function-keys-conf  
```
키보드 디바이스 번호 확인 방법  
dmesg | grep hidraw k380 
``` 

##  테스크탑 UI 변경  
```
sudo apt-get install xfce4
sudo apt-get install xubuntu-default-settings
```

## gpu 정보 받아오기 위해 nvidia 드라이버 설치  
방법 1)  
https://devyurim.github.io/development%20environment/ubuntu/2018/05/24/ubuntu-2.html  

방법 2)  
sofrware & update 에서 Additional Drivers 탭을 선택하면 설치 가능한 nvidia 드라이버들이 나열되어있다.  
선택하여 Apply Changes를 해줘도 된다.  

## python 삭제해서 UI 안 되었을 때 복구했던 방법  
https://askubuntu.com/questions/218919/i-accidentally-deleted-usr-bin-python-how-do-i-restore-it
