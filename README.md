# PyWinConsoleBuffer
ctypes wrapper for a console buffer for multi-line text writing and re-writing.



# Usage

The main usage is for moving the write cursor along the buffer to write and update text.

Example updating 3 lines of text:

```python
from console_buffer import ConsoleBuffer, get_console_handle
import random
import time

buffer = ConsoleBuffer(100, 3)  # 3 line buffer with width of 100
handle = get_console_handle()
while True:
    line_one = f'One: {random.random()}'
    line_two = f'Two: {random.random()}'
    line_three = f'Three: {random.random()}'
    for index, line in enumerate([line_one, line_two, line_three]):
        buffer.set_position(0, index)
        buffer.write(line)
    buffer.show(handle)
    time.sleep(0.1)
```


## TODO

- [ ] Implement a writeline that takes care of trailing whitespace (ensuring previous text does not dangle at the tail)  
- [ ] Get the properties of the console to determine the width/height of the console as potential default  
- [ ] Allow the buffer to start somewhere other than origin (0, 0)
- [ ] Factor the console handle as a default in show method
