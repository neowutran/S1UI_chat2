TCC modification
==================

About
------------
Allow TCC to simulate click on chat link

Where
-------------
S1UI_chat2.gpk

function : ```broadCast``` 
right after:  ```var _loc14_ = "[" + id + "]";```

Code generated
-----------

```
if(msgs.indexOf("tcc-map:") != -1)
{
      _loc14_ = msgs.split("tcc-map:");
      _locl4_ = _loc14_[1];
      ToGame_Chat_ClickLink("3",_locl4_);
}
```

Code
-------------
```
Push "tcc-map:" 1 register25 "indexOf"
CallMethod
Push -1
Equals2
Not
Not
If tccmap
Push "tcc-map:" 1 register25 "split"
CallMethod
StoreRegister 14
Pop
Push "_locl4_" register14 1
GetMember
SetVariable
Push "_locl4_"
GetVariable
Push "3" 2 "ToGame_Chat_ClickLink"
CallFunction
Pop
tccmap:
```
How to
--------------

- Extract the raw actionscript blob from the S1UI_chat2.gpk. Use this tool repacker https://github.com/GoneUp/GPK_RePack

![extract raw blob1](https://neowutran.ovh/updates/Screenshots/gpkedit1.png)

![extract raw blob2](https://neowutran.ovh/updates/Screenshots/gpkedit2.png)

- Open the extracted raw blob with Free Flash Decompiler https://www.free-decompiler.com/flash/ 
- Go to "DoAction" script

![ffd1](https://neowutran.ovh/updates/Screenshots/gpkedit3.png)

- Locate where you want to insert the code (for this patch, right after ```var _loc14_ = "[" + id + "]";``` in the function ```broadCast```  )
- Once you found the corresponding assembly (dooble click on the actionscript panel, it will send you to the corresponding line in the assembly view) , click on "edit P-code"

![ffd2](https://neowutran.ovh/updates/Screenshots/gpkedit4.png)


- Insert the assembly code right after the ```POP``` instruction
- Save
- Save as XXX.gfx
- Go back to GPK repacker tools
- Big ByteProp Import -> select the newly created .gfx file

![gpk1](https://neowutran.ovh/updates/Screenshots/gpkedit5.png)


- Main -> Save 

![gpk1](https://neowutran.ovh/updates/Screenshots/gpkedit6.png)


- Enjoy

WIP: todo: add screenshot & a real wiki
