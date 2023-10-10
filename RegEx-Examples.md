## RegEx Assertions to scrape html table

```RegEx
(?<=<t[hd]>)(?<Info>.*?)(?=<\/t[hd]>)
```

```Text
<table>
<th>Name</th><th>Dept</th><th>Manager</th><th>DateOfEmployment</th>
<tr><td>Bob</td><th>Sales</td><td>Fred</td><td>01-Feb-2000</td></tr>
<tr><td>Jill</td><th>IT</td><td>John</td><td>21-Mar-2010</td></tr>
</table
```

## RegEx Matching email addresses

```RegEx
\b[A-Za-z0-9_.-]+@[a-z0-9]+(\.[a-z0-9]+)+\b
```

```Text
Wiley Mcmanaman  
wmcmanaman0@cargocollective.com Male 
Frederica Hearl 
Fhearl1@surveymonkey.com
 Non-binary 
Rosemaria Kaser rkaser2@chicagotribune.com Female 
Monica 
Vanyakin mvanyakin3@sciencedirect.com 
Female 
Janean Syde jsyde4@blinklist.com Female
Gaylene Scotford gscotford5@utexas.edu 
Female
Alexis Liley aliley6@gizmodo.com Male 
Rhoda Nutt rnutt7@tuttocitta.it 
Female 
Issie Caulfield icaulfield8@i2i.jp 
Female 
Babette Dowers
 bdowers9@cafepress.com Female
Ilene Crann 
   icranna@zimbio.com Female 
Kellina Ketteringham
 kketteringhamb@csmonitor.com 
Female 
Sybyl Snowden
  ssnowdenc@addtoany.com Non-binary 
Roger Fattorini rfattorinid@flickr.com Male
Steve Skellon 
sskellone@dailymail.co.uk Male 
Freeman Daunter fdaunterf@sonet.ne.jp Male 
Joey Vossing jvossingg@nature.com Male 
Demetri Huffer dhufferh@amazonaws.com Male 
Kiele Castledine 
kcastledinei@networkadvertising.org.au Female
Hilliard Kinforth 
hkinforthj@dot.gov Male 
```

## RegEx Quiz 1

```RegEx
^[a-z0-9]+\.[a-z0-9]+@[a-z]{2,}(\.[a-z]{2,}){1,3}$
```

```Text
Match 
brent.denny@company.com
debbra.green@xyz.com.au
greg.parr2@qwerty.co.nz
Do not match
john@abc.com
betty.jones@abc.nsw.company.com.au
bill@a.c
```

## RegEx Quiz 2

```RegEx
(\b[A-Z]{4}-?[0-9]{6}\b)(?=.*[Ss]erial)
```

```Text
Match and Capture the serial number only
ZXER123456 Serial No. 
ZVES235562 serial #
ZFEU-789576 Serial number 
Do not match or capture
	ZFER1234567 serial number
	ZFERT123456 serial
	ASER321321 model number
```

## RegEx Backreference captures

```RegEx
<(strong>).*\1
```

```Text
<p>Hickory dickery doc 
<strong>three</strong> mice ran up the clock 
the clock <strong>struck</strong> one 
and the <strong>other two</strong> got away with minor injuries</p>
```

## RegEx Alternation

```RegEx
(they?)|(\bpr.*?\b)
```

```Text
In a world of code, they find their place,
A programmer's mind, a boundless space.
With lines and logic, they craft and create,
Solving problems, they innovate.

Through bugs and errors, they persist,
Debugging with a determined twist.
In the realm of bytes and screens so bright,
Programmers turn darkness into light.

 With keyboards clacking, they forge the way,
Coding through the night and into the day.
In a digital world, they're the guiding star,
The programmers, who dream and code, by far.
```

## RegEx Anchors - how they change with multiline option

```RegEx
^\b[IAWDS][a-z]+?\b
```

```Text
In a world of code, they find their place,
A programmer's mind, a boundless space.
With lines and logic, they craft and create,
Solving problems, they innovate.

Through bugs and errors, they persist,
Debugging with a determined twist.
In the realm of bytes and screens so bright,
Programmers turn darkness into light.

 With keyboards clacking, they forge the way,
Coding through the night and into the day.
In a digital world, they're the guiding star,
The programmers, who dream and code, by far.
```

## RegEx Exact Quantifiers

```RegEx
^.*Temp:\d{1,2} Pres:\d{1,4} Hum:\d{1,2}$
```

```Text
Sydney Temp:10 Pres:1013 Hum:68
Brisbane Temp:28 Pres:1030 Hum:79
Melbourne Temp:5 Pres:998 Hum:12
Perth Temp:123 Pres:9998 Hum:199
Hobart Temp:12 Pres:870 Hum:200
```


## RegEx Greedy and Lazy Quantifiers

```RegEx
<.+>
```

```Text
<html><body><p>To make the word <strong>emphasised</strong> strongly</p></body></html>
```


## RegEx Character Sets

```RegEx
[ae][h-s]
```

```Text
The rain in Spain falls mainly on the plane
Peter Piper picked a peck of pickled peppers
```


## RegEx Why is the second pe in peppers not matched

```RegEx Negated Character Set
p[^lor]
```

```Text
The rain in Spain falls mainly on the plane
Peter Piper picked a peck of pickled peppers pragmatically
```


## RegEx Turn off Global option to see the difference

```RegEx
i[cn]
```

```Text
The rain in spain falls mainly on the plane
Peter Piper picked a peck of pickled peppers
```

## RegEx Positive Lookahead Assertions

```RegEx
\b\d+\b(?= +[Yy]ears +old)
```

```Text
Bob is my name, my postcode is 4211 and I am 20  Years old.
Barbara is my name, my postcode is 3412 and I am 46 years old.
Christine is my name, my postcode is 2211 and I am 19  years old.
Bill is my name, my postcode is 7123 and I am 62 years old.
Greg is my name, my postcode is 2212 and I am 41 years  old.
```

## RegEx Lookbehind Assertions

```RegEx
(?<=@)[a-z]+(\.[a-z]+)+
```

```Text
brent.denny@companyb.com
joanj@companya.com
bboo@companyc.com.au
grant@companyd.qld.gov.au
```

## RegEx Lookahead Assertions

```RegEx
\b.*\b(?=@)
```

```Text
brent.denny@companyb.com
joanj@companya.com
bboo@companyc.com.au
grant@companyd.qld.gov.au
bill#companyx.gov.au
```
