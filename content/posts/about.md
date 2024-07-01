+++
title = "About."
lastmod = 2024-07-01T03:29:39-05:00
categories = ["emacs", "hugo"]
draft = false
+++

## Initial header. {#initial-header-dot}

Pellentesque dapibus suscipit ligula.  Donec posuere augue in quam.  Etiam vel tortor sodales tellus ultricies commodo.  Suspendisse potenti.  Aenean in sem ac leo mollis blandit.  Donec neque quam, dignissim in, mollis nec, sagittis eu, wisi.  Phasellus lacus.  Etiam laoreet quam sed arcu.  Phasellus at dui in ligula mollis ultricies.  Integer placerat tristique nisl.  Praesent augue.  Fusce commodo.  Vestibulum convallis, lorem a tempus semper, dui dui euismod elit, vitae placerat urna tortor vitae lacus.  Nullam libero mauris, consequat quis, varius et, dictum id, arcu.  Mauris mollis tincidunt felis.  Aliquam feugiat tellus ut neque.  Nulla facilisis, risus a rhoncus fermentum, tellus tellus lacinia purus, et dictum nunc justo sit amet elit.


## Code. {#code-dot}

```python
import pylogix, pycomm3
from pylogix import PLC
from pycomm3 import LogixDriver

# This script check what devices are connected in this node.
with PLC() as plc:
    devices = plc.Discover()
    if not devices.Value:
        print("Not connected to any NODE!!")
        pass
    else:
        for device in devices.Value:
            print(device.ProductName, device.Revision)

```
