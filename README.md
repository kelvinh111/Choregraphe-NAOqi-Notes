# Choregraphe / NAOqi Notes

Global vars
---

#### Box 1:
```
from naoqi import ALProxy

alm = ALProxy('ALMemory')
alm.insertData('my_var', 999)
```

#### Box 2:
```
alm = ALProxy('ALMemory')
my_var = alm.getData('my_var')
self.log(my_var) #999
```

---

Get project file path
---
```
onLoad
self.framemanager = ALProxy("ALFrameManager")

self.framemanager.getBehaviorPath(self.behaviorId) + self.getParameter("File name")
```

---


Use external python file
---

**Get project file path first (Above one).**

#### Box 1:

```
onInput_onStart
import sys
if self.folderName not in sys.path:
    sys.path.insert(0, self.folderName)

onUnload
import sys
if self.folderName and self.folderName in sys.path:
    sys.path.remove(self.folderName)
```

#### Box 2:
Just import any python file. 
i.e.  test.py at project root, then:
```
import test
```
