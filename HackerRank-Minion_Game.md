

Refer: https://www.hackerrank.com/challenges/the-minion-game/problem?h_r=next-challenge&h_v=zen


# Solution-1 : High time complexity

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
elif score_vowel == score_c:
    print("Draw")
else:
    print(f"Stuart {score_c}")
```


### Output
```Stuart 12```


---

# Solution-2 : Less time complexity

Above, the word list and the word-count frequency is an unecessary by-product as its not used in the final output.
So we just need to focus on counting the words rather than storing the sub-words...
```none
Count of sub-words for 'cat' :
Starting with 'c' => ['c','ca','cat']
Starting with 'a' => ['a','at']
Starting with 't' => ['t'] 
```

From above we see word count is substring length, i.e. 'cat' => 3 sub-words, 'at' => 2 sub-words, etc...

```
string = 'BANANA'
vowel =['A','E','I','O','U']
S=0
K=0
for i in range(len(string)):
    print(string[i],len(string)-i)
    if string[i] in vowel:
        K+= len(string)-i
    else:
        S+=len(string)-i
if S>K:
    print("Stuart"+" "+ "%d" % S)
elif K>S:
    print("Kevin"+" "+'%d' % K)
else:
    print("Draw")
```
