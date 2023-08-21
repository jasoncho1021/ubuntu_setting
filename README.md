## gpu 사용량 실기간으로 받아오기 위한 nvidia 드라이버 설치  
방법 1)  
https://devyurim.github.io/development%20environment/ubuntu/2018/05/24/ubuntu-2.html  

방법 2)  
sofrware & update 에서 Additional Drivers 탭을 선택하면 설치 가능한 nvidia 드라이버들이 나열되어있다.  
선택하여 Apply Changes를 해줘도 된다.  

## 베터리 사용량 늘리기
1-1) BIOS: primary battery charge configuration 80% -> 100%  
1-2) nvidia -> 내장 intel로 전환  
https://jjeaby.medium.com/xps15-for-ubuntu-md-aab8b42073d3  
https://medium.com/@tomwwright/better-battery-life-on-ubuntu-17-10-4588b7f72def

## python 삭제해서 UI 안 되었을 때 복구했던 방법  
https://askubuntu.com/questions/218919/i-accidentally-deleted-usr-bin-python-how-do-i-restore-it  

## 트랙패드 디바이스  변경
```
sudo apt-get install xserver-xorg-input-libinput
sudo apt-get remove --purge xserver-xorg-input-synaptics
sudo reboot
```
https://github.com/rcasero/doc/wiki/Ubuntu-linux-on-Dell-XPS-15-(9560)#touchpad  

## 트랙패드 제스처 추가
https://github.com/iberianpig/fusuma  
~/.config/fusuma/config.yml
```
swipe:
  3:
    left:
      command: 'xdotool key ctrl+alt+l'
    right:
      command: 'xdotool key ctrl+alt+j'
    up:
      command: 'xdotool key super+w'
    down:
      command: 'xdotool key super+s'
  4:
    left:
      command: ''
    right:
      command: ''
    up:
      command: 'xdotool key super+shift+w'
    down:
      command: ''
pinch:
  2:
    in:
      command: ''
      threshold: 0.1
    out:
      command: ''
      threshold: 0.1
 
threshold:
  swipe: 1
  pinch: 1
 
interval:
  swipe: 1
  pinch: 1
```

## k380 키보드 fn키 lock 걸기  
https://github.com/jergusg/k380-function-keys-conf  
```
키보드 디바이스 번호 확인 방법  
dmesg | grep hidraw k380 
``` 
## CapsLock + ikjl키 -> 상하좌우 방향키로 맵핑  
/usr/share/X11/xkb/symbols/pc    
```
default  partial alphanumeric_keys modifier_keys
xkb_symbols "pc105" {

    key <ESC>  {	[ Escape		]	};
    // The extra key on many European keyboards:
    key <LSGT> {	[ less, greater, bar, brokenbar ] };

    // The following keys are common to all layouts.
    key <BKSL> {	[ backslash,	bar	]	};
    key <SPCE> {	[ 	 space		]	};

    include "srvr_ctrl(fkey2vt)"
    include "pc(editing)"
    include "keypad(x11)"

    key <BKSP> {	[ BackSpace, BackSpace	]	};

    key  <TAB> {	[ Tab,	ISO_Left_Tab	]	};
    key <RTRN> {	[ Return		]	};

    key <CAPS> {	[ ISO_Level3_Shift	]	};
    key <NMLK> {	[ Num_Lock 		]	};

    key <LFSH> {	[ Shift_L		]	};
    key <LCTL> {	[ Control_L		]	};
    key <LWIN> {	[ Super_L		]	};

    key <RTSH> {	[ Shift_R		]	};
    key <RCTL> {	[ Control_R		]	};
    key <RWIN> {	[ Multi_key	]	};
    key <MENU> {	[ Menu			]	};

    // Beginning of modifier mappings.
    modifier_map Shift  { Shift_L, Shift_R };
    modifier_map Lock   { Caps_Lock };
    modifier_map Control{ Control_L, Control_R };
    modifier_map Mod2   { Num_Lock };
    modifier_map Mod4   { Super_L, Super_R };

    // Fake keys for virtual<->real modifiers mapping:
    key <LVL3> {	[ ISO_Level3_Shift	]	};
    key <MDSW> {	[ Mode_switch 		]	};
    modifier_map Mod5   { <LVL3>, <MDSW> };

    key <ALT>  {	[ NoSymbol, Alt_L	]	};
    include "altwin(meta_alt)"

    key <META> {	[ NoSymbol, Meta_L	]	};
    modifier_map Mod1   { <META> };

    key <SUPR> {	[ NoSymbol, Super_L	]	};
    modifier_map Mod4   { <SUPR> };

    key <HYPR> {	[ NoSymbol, Hyper_L	]	};
    modifier_map Mod4   { <HYPR> };
    // End of modifier mappings.

    key <OUTP> { [ XF86Display ] };
    key <KITG> { [ XF86KbdLightOnOff ] };
    key <KIDN> { [ XF86KbdBrightnessDown ] };
    key <KIUP> { [ XF86KbdBrightnessUp ] };

    key <AD08> { type="THREE_LEVEL", [ i, I, Up  ] };
    key <AC07> { type="THREE_LEVEL", [ j, J, Left ] };
    key <AC08> { type="THREE_LEVEL", [ k, K, Down ] };
    key <AC09> { type="THREE_LEVEL", [ l, L, Right ] };
    key <AC06> { type="THREE_LEVEL", [ h, H, Home ] };
    key <AB06> { type="THREE_LEVEL", [ n, N, End ] };
};

hidden partial alphanumeric_keys
xkb_symbols "editing" {
    key <PRSC> {
	type= "PC_ALT_LEVEL2",
	symbols[Group1]= [ Print, Sys_Req ]
    };
    key <SCLK> {	[  Scroll_Lock		]	};
    key <PAUS> {
	type= "PC_CONTROL_LEVEL2",
	symbols[Group1]= [ Pause, Break ]
    };
    key  <INS> {	[  Insert		]	};
    key <HOME> {	[  Home			]	};
    key <PGUP> {	[  Prior		]	};
    key <DELE> {	[  Delete		]	};
    key  <END> {	[  End			]	};
    key <PGDN> {	[  Next			]	};

    key   <UP> {	[  Up			]	};
    key <LEFT> {	[  Left			]	};
    key <DOWN> {	[  Down			]	};
    key <RGHT> {	[  Right		]	};
};
```
```
key <CAPS> { [ ISO_Level3_Shift ] };

key <AC06>  { type="THREE_LEVEL", [   h,   H, Left  ]   }; 
key <AC07>  { type="THREE_LEVEL", [   j,   J, Down  ]   }; 
key <AC08>  { type="THREE_LEVEL", [   k,   K, Up    ]   }; 
key <AC09>  { type="THREE_LEVEL", [   l,   L, Right ]   }; 
```

/usr/share/X11/xkb/types/iso9995  
```
partial default xkb_types "default" {

    // A key type which can be used to implement
    // an ISO9995-style level-three shift.

    virtual_modifiers LevelThree;

    type "THREE_LEVEL" {
	modifiers = Shift+LevelThree;
	map[None] = Level1;
	map[Shift] = Level2;
	map[LevelThree] = Level3;
	map[Shift+LevelThree] = Level3;
	preserve[Shift+LevelThree] = Shift;
	level_name[Level1] = "Base";
	level_name[Level2] = "Shift";
	level_name[Level3] = "Level3";
    };
};
```
```
preserve[LevelThree+Shift] = Shift;  
```
https://askubuntu.com/questions/533719/custom-keyboard-layout-to-use-h-j-k-l-as-arrows-not-working-properly/1048906#1048906  
  

##  테스크탑 UI 변경  
```
sudo apt-get install xfce4
sudo apt-get install xubuntu-default-settings
```


