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
``` python
import sys
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Button, Slider
# The parametrized function to be plotted
def f(t, amplitude, frequency):
    return amplitude * np.sin(2 * np.pi * frequency * t)
# The function to be called anytime a slider's value changes

def main():
    t = np.linspace(0, 1, 1000)

    # Define initial parameters
    init_amplitude = 5
    init_frequency = 3
    # Create the figure and the line that we will manipulate
    fig, ax = plt.subplots()
    line, = ax.plot(t, f(t, init_amplitude, init_frequency), lw=2)
    ax.set_xlabel('Time [s]')

    # adjust the main plot to make room for the sliders
    fig.subplots_adjust(left=0.25, bottom=0.25)

    # Make a horizontal slider to control the frequency.
    axfreq = fig.add_axes([0.25, 0.1, 0.65, 0.03])
    freq_slider = Slider(
        ax=axfreq,
        label='Frequency [Hz]',
        valmin=0.1,
        valmax=30,
        valinit=init_frequency,
    )

    # Make a vertically oriented slider to control the amplitude
    axamp = fig.add_axes([0.1, 0.25, 0.0225, 0.63])
    amp_slider = Slider(
        ax=axamp,
        label="Amplitude",
        valmin=0,
        valmax=10,
        valinit=init_amplitude,
        orientation="vertical"
    )
    def update(val):
        line.set_ydata(f(t, amp_slider.val, freq_slider.val))
        fig.canvas.draw_idle()

    def reset(event):
        freq_slider.reset()
        amp_slider.reset()
    # register the update function with each slider
    freq_slider.on_changed(update)
    amp_slider.on_changed(update)

    resetax = fig.add_axes([0.8, 0.025, 0.1, 0.04])
    button = Button(resetax, 'Reset', hovercolor='0.975')
    button.on_clicked(reset)   

    plt.show()
main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)