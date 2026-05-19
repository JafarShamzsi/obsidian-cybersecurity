#quicknotes
```
#Without multiprocessing
from time import sleep

def process(x):
	sleep(1)
	return x * 2

data = [process(x) for x in a range(4)]

#with multiprocessing</font>
from multiprocessing import pool
with Pool() as pool:
	data = pool.map(process, range(4))
```
