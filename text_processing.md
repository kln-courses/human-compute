# Introduction to Text Processing in Python #


## Regular Expressions ##

Removing numbers
```py
import re
str1 = 'string with456, some111 hello 888 numbers'
txt = re.sub('[0-9]+', '', str1)
txt = re.sub('\d+', '', str1)
print(txt)
```

Splitting with multiple separator (numbers, comma, spaces, plus, colon)
```py
str1 = 'string with456, some111:hello 888 num+bers'
txt = re.split('[0-9,:+\s]+',str1)
print(txt)
```

Find all numbers
```py
str1 = 'string with456, some111:hello 888 num+bers'
txt = re.findall('\d+', str1)
print(txt)
```

Find 2 related words with up to 20 characters between them
```py
testy = 'The quick brown fox jumps over the lazy dog'
m = re.search(r"(quick|slow).{1,20}(fox|camel)", testy)
if m:
    print('Matched',m.groups())
    print('Starting at', m.start())
    print('Ending at', m.end())
```

## Using Dedicated Packages ##

Removing punctuation
```py
import string

mess = 'strin.g with, so!me: punct,uation+'
newmess = [char for char in mess if char not in string.punctuation]
newmess = ''.join(newmess)

print(nopunc)
```
### NLTK ###

NLTK - download data
```py
import nltk
nltk.download('stopwords')
```

NLTK - stopword filtering
```py
from nltk.corpus import stopwords

allstopwords = stopwords.words('english')
inputmessage = "I have to see the code today"
outmessage = [word for word in inputmessage.split() if word.lower() not in allstopwords]
print(outmessage)
```

### scikit-learn ###
```py
data = ['hello world',
        'have a good day',
        'hello all',
        'how are you',
        'hello and have a nice day'
        ]
```

Build vocabulary
```py
from sklearn.feature_extraction.text import CountVectorizer

trans = CountVectorizer().fit(data)
print(trans.vocabulary_)
```

Transform to bag-of-words
```py
tr = trans.transform(data)
print (tr)
```

Vector space
```py
tr.toarray()
```

Count words
```py
tr.toarray().sum(axis=0)
```
