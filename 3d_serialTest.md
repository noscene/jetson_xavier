```python
# apt install python3-serial
# sudo adduser sven dialout
# sudo chown :sven /dev/ttyACM0
# https://www.mpminidelta.com/starting_ending_g-code_scripts
import serial
import time
```


```python
ser = serial.Serial('/dev/ttyACM0', 115200)
time.sleep(2)
```


```python
# Go Home x,y,z = 0
ser.write(b"G28\r\n")
```




    5




```python
# drive Up for better cam View
ser.write(b"G90\r\n")
time.sleep(2)
ser.write(b"G1 Z50 F3600\r\n")
```




    14




```python
def driveto(pos):
    x = int(pos[0])
    y = int(pos[1])
    if(x<10):
        print("Bad x:",x)
        return
    if(x>100):
        print("Bad x:",x)
        return
    if(y<10):
        print("Bad y:",y)
        return
    if(y>100):
        print("Bad y:",y)
        return
    gcode="G1 X"+ str(x) + " Y"+ str(y) +" F3600\r\n"
    print(gcode)
    ser.write(gcode.encode('raw_unicode_escape'))
def motoroff():
    ser.write(b"M84\r\n")
```


```python
driveto((70,70))
```

    G1 X70 Y70 F3600
    



```python

```
