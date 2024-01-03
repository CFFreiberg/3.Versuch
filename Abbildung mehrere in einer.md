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


import: https://github.com/liascript/CodeRunner

import: https://raw.githubusercontent.com/LiaTemplates/Pyodide/master/README.md


-->

# Abbildung mehrere in einer

``` python
# Quelle: https://matplotlib.org/stable/gallery/widgets/slider_snap_demo.html




import matplotlib.pyplot as plt
import numpy as np


# evenly sampled time at 200ms intervals
t = np.arange(0., 5., 0.2)

def main():
# red dashes, blue squares and green triangles
    plt.plot(t, t, 'r--', t, t**2, 'bs', t, t**3, 'g^')
    plt.show()

main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)