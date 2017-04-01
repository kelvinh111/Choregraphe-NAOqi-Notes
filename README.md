# Choregraphe / NAOqi Notes

Global vars
---

#### Box 1:
```python
# may need to import ALProxy manually
from naoqi import ALProxy

alm = ALProxy('ALMemory')
alm.insertData('my_var', 999)
```

#### Box 2:
```python
alm = ALProxy('ALMemory')
my_var = alm.getData('my_var')
self.log(my_var) #999
```

---

Get project file path
---
```python
# onLoad
self.framemanager = ALProxy("ALFrameManager")

# Notice the "..\" at the end
project_root_path = self.framemanager.getBehaviorPath(self.behaviorId) + "..\"
```

---


Use external python file
---

#### Box 1:

```python
def onLoad(self):
    self.framemanager = ALProxy("ALFrameManager")
    #self.folderName = None

def onInput_onStart(self):
    self.folderName = self.framemanager.getBehaviorPath(self.behaviorId) + self.getParameter("File name")
    import sys
    if self.folderName not in sys.path:
        sys.path.insert(0, self.folderName)
    self.onStopped()

def onUnload(self):
    import sys
    if self.folderName and self.folderName in sys.path:
        sys.path.remove(self.folderName)
```

#### Box 2:
Just import any python file. 
i.e.  test.py at project root, then:
```python
import test
```
