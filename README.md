<!--
author:   Claudia Funke

email:    claudia.funke@physik.tu-freiberg.de

version:  0.0.1

language: de

narrator: Deutsch Female

comment:  Struktur der Materie Übung 7

@style
.lia-toc__bottom {
    display: none;
}
@end


import: https://raw.githubusercontent.com/liaTemplates/KekuleJS/master/README.md

import: https://github.com/liascript/CodeRunner

import: https://raw.githubusercontent.com/LiaTemplates/Pyodide/master/README.md


-->




# 3.Versuch
3.Versuch Lehre


``` py
import numpy as np
import matplotlib.pyplot as plt
def main():
    variable = np.linspace(-1,1,100)
    m=0.1
    fsquared = np.sin(0.5*np.pi*variable*m)**2//np.sin(0.5*np.pi*variable)**2
    plt.plot(variable, fsquared)
    plt.show()

main()
```
@LIA.eval(`["main.py"]`, `none`, `python3 main.py`, `*.py`)


```python
import numpy as np
import matplotlib.pyplot as plt
for i in range(3):
  print("Hallo World ", i)
variable = np.linspace(-1,1,100)
m=0.1
fsquared = np.sin(0.5*np.pi*variable*m)**2//np.sin(0.5*np.pi*variable)**2
plt.plot(variable, fsquared)
plt.show()
```
@LIA.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)
```
import sys
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Button, Slider
def main():
    for i in range(5):
	    print("Hello", 'World #', i)

    t = np.arange(0.0, 2.0, 0.01)
    s = np.sin(2 * np.pi * t)

    fig, ax = plt.subplots()
    ax.plot(t, s)

    ax.grid(True, linestyle='-.')
    ax.tick_params(labelcolor='r', labelsize='medium', width=3)

    plt.show()
main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)