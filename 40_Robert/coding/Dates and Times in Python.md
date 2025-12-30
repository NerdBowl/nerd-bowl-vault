[[Dates and Times]] are weird. An large collection of exceptions and irregularities make handling dates and times surprisingly complex. In this document we will try to describe how to handle dates and times properly in python. The same principles apply to any other programming language aswell.

An event happens at one specific, absolute, moment in the universe. We can describe this point in time in two ways: 
1. Absolute Time: the number of seconds since a reference point (usually the Unix Epoch). 
2. Civil Time: the combination of a date, a time, and a timezone ("Clocks and Calendars").

We will go trough a list of operations you might want to perform, describe the operation in detail, describe how it should be calculated, and how you can perform the operation properly and easily in python. Lets go.

We will use the following packages from the python standard library in the following examples.
```python
import time 
from datetime import datetime, timedelta, timezone
from zoneinfo import ZoneInfo # IANA timezone support
from calendar import Calendar
```

#### Describing a point in time.
In python, `datetime` objects are either:
- **Naive**: without timezone info. This is dangerous, its just assumes "whatever the local the computer thinks".
- **Aware**: has a `tzinfo` object attached. This is the correct way.


