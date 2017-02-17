[![PyPI](https://img.shields.io/badge/PyPi-v1.2.1-f39f37.svg)](https://pypi.python.org/pypi/hackerrank-sdk)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/angular/angular.js/blob/master/LICENSE.txt)

#                                                     HackerRank SDK

####What is this SDK all about?
Using the hackerrank sdk you can execute any code online along with passing the test cases. 
For example, a teacher wants to evaluate every student's submission by sending over the ***untrusted code*** of the student, 
over to the Hackerrank servers to execute, along with the test cases in the form of a list of strings. It will return the output back to your console. Let us have a look at the walkthrough.

[This](https://www.hackerrank.com/api/docs) Unofficial Python Client supports interaction with the HackerRank API. It provides integration with HackerRank API for compiling and running code in several languages. You need to have an API key in order to access the API. It can be accessed via a simple API key based authorization process.[Get your api-key from here](https://www.hackerrank.com/api/docs).
To Get Started : 



![GetStarted](https://github.com/AdityaOli/Projects/blob/master/Execute%20untrusted%20code%20online%20using%20the%20hackerrank%20API/Images/Tut%20img%201.PNG?raw=true)

After clicking on Get Started button, you need to type in the details on the next page.


![Details](https://github.com/AdityaOli/Execute-untrusted-code-online-using-the-hackerrank-API/blob/master/Images/Tut%20img%201.PNG?raw=true)


All set, Click on Generate API Code button. And!!!!


![API](https://github.com/AdityaOli/Execute-untrusted-code-online-using-the-hackerrank-API/blob/master/Images/Tut%20img%203.PNG?raw=true)

You have your API key ready to use.

The code mentioned is Python 2, but Python 3 compatible.

####If you do not have pip added to your path(usually on windows), Navigate to the folder where python has been installed, then enter
####```cd Scripts```
From here you can Shift+right click -> open command window here. And then you can opt for the fast install method.

## Installation

Fast install:

        pip install hackerrank-sdk
    
![Fast Install](https://github.com/AdityaOli/Execute-untrusted-code-online-using-the-hackerrank-API/blob/master/Images/Tut%20img%204.PNG?raw=true)


For a manual install download this package: https://pypi.python.org/pypi/hackerrank-sdk
    
    unzip <hackerrank-sdk version>
    rm <hackerrank-sdk version>             #delete the zip
    cd hackerrank-sdk-master                #navigate into the extracted file


Install the package:

        python setup.py install

## Code Examples
```python

from hackerrank.HackerRankAPI import HackerRankAPI

API_KEY = ''  #your API-KEY here

compiler = HackerRankAPI(api_key = API_KEY)

print compiler.supportedlanguages()     #prints a list of supported languages


source = '''print "Hello World!"'''    #give your source code here

'''
Alternatively,you can copy existing files to source this way:
with open(file_name,'r') as f:
     source = f.read()
'''     

result = compiler.run({'source': source,
                       'lang':'python'     
                       })


print(result.output,result.time,result.memory,result.message)    #get different variables associated with the result

```
***Testcases are passed as a list of strings.***

Now after you input your API key in the place mentioned above in the code, you will get the error when you run the code.

```python
Traceback (most recent call last/):
  File "<blah blah blah>/Test.py", line 1, in <module>
    from hackerrank.HackerRankAPI import HackerRankAPI
  File "<blah blah blah>\Python\Python35-32\lib\site-packages\hackerrank\HackerRankAPI.py", line 2, in <module>
    import requests
ImportError: No module named 'requests'
```

So to counter this, all you need is to install the ***```requests```*** package.
```
    pip install requests
```
In the same manner, any missing packages can be installed using pip, or by downloading the package and then installing it using 
the setup.py method.


Here is another example which shows how to give testcases to the compiler:
```python
from hackerrank.HackerRankAPI import HackerRankAPI

API_KEY = ''  # Your API-KEY here

compiler = HackerRankAPI(api_key = API_KEY)

source ='''
N, M = map(int,raw_input().split())
for i in xrange(1,N,2):
    print (".|."*i).center(M,'-')

print "WELCOME".center(M,'-')
for i in xrange(N-2,-1,-2):
    print (".|."*i).center(M,'-')
'''

result = compiler.run({'source': source,
                       'lang':'python',
                       'testcases':["9 27"]
                       })

print(result.output[0])
```
Here is the output:

![output](https://github.com/AdityaOli/Execute-untrusted-code-online-using-the-hackerrank-API/blob/master/Images/Tut%20img%205.PNG?raw=true)
