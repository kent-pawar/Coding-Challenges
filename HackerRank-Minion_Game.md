

Refer: https://www.hackerrank.com/challenges/the-minion-game/problem?h_r=next-challenge&h_v=zen

# Solution
```python
# Get all possible combination of words
s = 'BANANA'
s_len = len(s)
words = []
for j in range(s_len+1):
    for i in range(s_len+1):
        if j<i:
            words.append( s[j:i] )
            print(j*'-' + s[j:i] + (s_len - i)*'-')
```

### Output: 
```
B-----
BA----
BAN---
BANA--
BANAN-
BANANA
-A----
-AN---
-ANA--
-ANAN-
-ANANA
--N---
--NA--
--NAN-
--NANA
---A--
---AN-
---ANA
----N-
----NA
-----A
```


Next, Get word-count frequency
```python
# Get word count frequency
counts = {}
for i in words:
    if i in counts:
        counts[i] += 1
    else:
        counts[i] = 1
(counts)
```

### Output: 
```
{'B': 1,
 'BA': 1,
 'BAN': 1,
 'BANA': 1,
 'BANAN': 1,
 'BANANA': 1,
 'A': 3,
 'AN': 2,
 'ANA': 2,
 'ANAN': 1,
 'ANANA': 1,
 'N': 2,
 'NA': 2,
 'NAN': 1,
 'NANA': 1}
```

Finally, tally up the word counts ...
```
v = 'AEIOU'
v = [i for i in v]

score_vowel = 0
score_c = 0 # consonants

for i in counts:
    if i[0:1] in v:
        score_vowel += counts[i]
    else:
        score_c += counts[i]

if score_vowel > score_c:
    print(f"Kevin {score_vowel}")
else:
    print(f"Stuart {score_c}")
```


### Output
```Stuart 12```
