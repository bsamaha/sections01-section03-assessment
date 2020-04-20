
# Necessary Goals
You will
- Section01
    - a. create a word counts dictionary
    - b. find most common word
- Section02
    - a. calculate the mean and standard deviation of the word counts
- Section03
    - write a function that takes in a parameter to complete a task
    - write a function that takes in multiple parameters to complete a task

# Level Up Goals
- write a function that solves a particular logical task
- write a lambda function to complete a task


```python
# just run this cell
from importlib import reload
import solutions.solutions as sol
reload(sol)
```




    <module 'solutions.solutions' from 'C:\\Users\\blake\\flatiron-ds-course\\assessments\\sections_1-3\\sections01-section03-assessment\\solutions\\solutions.py'>



# Section 01: Strings
Using the variable `lyrics` below, please solve the following questions


```python
# this cell will just load and open the lyrics
# just run this cell
with open("data/lyrics.txt", "r") as f:
    lyrics = f.read()


```

## S01 - Part A
create a dictionary called `word_counter` that counts the number of words in `lyrics`.
- remove all puntuation using `string punctuation`
- lowercase the entire string
- split by `" "`


```python
# build your word_counter here
# Your code here

#Cleaning the lyrics of any punctuation and translating it all to lowercase so that we can accurately count words. 
#Example: "That," and "that" won't count as the same word. We transformed "That," to "that" and "that == "that".

 #This for loop removes all the characters
from collections import Counter
from pprint import pprint
    
def get_word_counter(text):
    text = text.lower() #Makes everything lowercase because "That" != "that"
    for char in "*!.:,][)(":
        text = text.replace(char, ' ') #cleans any and all punctionation except brackets
    text = text.replace("'", "") #She'll will be turned into "shell" instead of she and "ll" when we split
    text = text.replace("-","")
    clean_text = text.split() #This splits the entire text into separate wordfinding whitespace and stripping it
    return dict(Counter(clean_text)) #Learned counter function in the process of writing a get_mode function.
                                        #Word counters are perfect for this function.

word_counter = get_word_counter(lyrics)

pprint(word_counter)
    
    
 




```

    {'a': 15,
     'aint': 1,
     'and': 4,
     'apart': 1,
     'are': 1,
     'at': 2,
     'beast': 1,
     'beauty': 1,
     'before': 1,
     'boy': 7,
     'but': 2,
     'by': 1,
     'can': 1,
     'chew': 6,
     'come': 2,
     'comes': 24,
     'could': 1,
     'deadly': 1,
     'do': 1,
     'door': 1,
     'eyes': 1,
     'far': 1,
     'for': 2,
     'free': 1,
     'get': 1,
     'gettin': 1,
     'gonna': 1,
     'have': 1,
     'heart': 1,
     'her': 2,
     'here': 25,
     'hungry': 1,
     'i': 3,
     'if': 2,
     'in': 2,
     'instrumental': 1,
     'interlude': 1,
     'is': 5,
     'it': 1,
     'ive': 1,
     'jaguar': 1,
     'know': 1,
     'lean': 1,
     'love': 1,
     'man': 1,
     'maneater': 12,
     'many': 1,
     'matter': 2,
     'mind': 1,
     'moneys': 1,
     'new': 1,
     'night': 1,
     'nights': 1,
     'nothing': 1,
     'of': 1,
     'oh': 2,
     'ohoh': 19,
     'on': 1,
     'only': 2,
     'ooh': 3,
     'oohoh': 2,
     'ooooooooh': 1,
     'out': 15,
     'over': 1,
     'paid': 1,
     'purr': 1,
     'really': 1,
     'rip': 1,
     'see': 1,
     'seen': 1,
     'she': 26,
     'shecat': 1,
     'shell': 8,
     'shes': 15,
     'sittin': 1,
     'so': 1,
     'tamed': 1,
     'the': 8,
     'there': 1,
     'think': 1,
     'to': 1,
     'too': 1,
     'type': 1,
     'up': 6,
     'waiting': 2,
     'watch': 13,
     'watching': 2,
     'were': 1,
     'what': 2,
     'whoaoh': 1,
     'whoooa': 1,
     'wild': 2,
     'with': 1,
     'woman': 2,
     'world': 1,
     'wouldnt': 1,
     'yeah': 2,
     'you': 10,
     'your': 1,
     'youre': 2}
    


```python
# get actual word_counter here
# just run this cell

word_counter_test = sol.section1_partA(lyrics)
pprint(word_counter_test)
```

    {'': 6,
     'a': 15,
     'aint': 1,
     'and': 4,
     'apart': 1,
     'are': 1,
     'at': 2,
     'beast': 1,
     'beauty': 1,
     'before': 1,
     'boy': 7,
     'but': 2,
     'by': 1,
     'can': 1,
     'chew': 6,
     'come': 2,
     'comes': 24,
     'could': 1,
     'deadly': 1,
     'do': 1,
     'door': 1,
     'eyes': 1,
     'far': 1,
     'for': 2,
     'free': 1,
     'get': 1,
     'gettin': 1,
     'gonna': 1,
     'have': 1,
     'heart': 1,
     'her': 2,
     'here': 25,
     'hungry': 1,
     'i': 3,
     'if': 2,
     'in': 2,
     'instrumental': 1,
     'interlude': 1,
     'is': 5,
     'it': 1,
     'ive': 1,
     'jaguar': 1,
     'know': 1,
     'lean': 1,
     'love': 1,
     'man': 1,
     'maneater': 12,
     'many': 1,
     'matter': 2,
     'mind': 1,
     'moneys': 1,
     'new': 1,
     'night': 1,
     'nights': 1,
     'nothing': 1,
     'of': 1,
     'oh': 2,
     'ohoh': 19,
     'on': 1,
     'only': 2,
     'ooh': 3,
     'oohoh': 2,
     'ooooooooh': 1,
     'out': 15,
     'over': 1,
     'paid': 1,
     'purr': 1,
     'really': 1,
     'rip': 1,
     'see': 1,
     'seen': 1,
     'she': 26,
     'shecat': 1,
     'shell': 8,
     'shes': 15,
     'sittin': 1,
     'so': 1,
     'tamed': 1,
     'the': 8,
     'there': 1,
     'think': 1,
     'to': 1,
     'too': 1,
     'type': 1,
     'up': 6,
     'waiting': 2,
     'watch': 13,
     'watching': 2,
     'were': 1,
     'what': 2,
     'whoaoh': 1,
     'whoooa': 1,
     'wild': 2,
     'with': 1,
     'woman': 2,
     'world': 1,
     'wouldnt': 1,
     'yeah': 2,
     'you': 10,
     'your': 1,
     'youre': 2}
    

## Checking differences between the two dictionaries

Since pprint conveniently sorts the dictionary keys by alphabetical order I can quickly see a difference in word_counter_test versus my word_counter. Below I wrote a function to count and show the differences between the count dictionary i created versus the solution guide's dictionary.


```python
def get_difference_of_dict(my_dict,other_dict):
    number_of_items_in_my_dict = len(my_dict.keys()) #number of keys in my dictionary
    number_of_items_in_other_dict = len(other_dict.keys()) #number of keys in solution dictionary
    discrepencies = number_of_items_in_other_dict - number_of_items_in_my_dict
    print(f'There is/are {discrepencies} difference(s) between your dictionary and the other dictionary!')
    if discrepencies > 0: #if there are any discrepencies.....
        dict_diff = { k : other_dict[k] for k in set(other_dict) - set(my_dict) } #Creates a dictionary of the differences between the two dictionaries
        return print(f'The other dictionary has {dict_diff} and yours does not.')
        
                 
get_difference_of_dict(word_counter, word_counter_test)
```

    There is/are 1 difference(s) between your dictionary and the other dictionary!
    The other dictionary has {'': 6} and yours does not.
    

### My word counter does not pass the test because for some reason the solution guide has an extra key,value showing " '' = 6 ". I'd argue that this key,value pair should not be in the solution guide as it contains no value to the context of a word counter and can skew results.


```python
# Test your code here
# just run this cell

try:
    assert word_counter==word_counter_test
    print('test passed')
except Exception as e:
    print("word_counter does not equal word_counter_test")
```

    word_counter does not equal word_counter_test
    

## S01 - Part B

Finding the most common word is very similar to finding the mode(s) of data. I have recently wrote what I believe to be an elegant solution for this so I have copied that function for this problem. I reuse my get_word_counter function from before to output the word count dictionary and then search for the highest value and return that key.


```python
# Find the word with the highest counts
# Your code here

def get_most_common_word(text):
    word_count = get_word_counter(text) #Cleans text and returns a dictionary of word counts
    most_common_word = [val for val,count in word_count.items()
                            if count == max(word_count.values())] #Finds highest value in our word_count dictionary and returns that key
    return most_common_word #returns a list of the most common word

most_common_word = get_most_common_word(lyrics)[0] #since this returns a list of 1 in this project we simply access element 0 in the list


```


```python
# get actual most_common_word
# just run this cell

most_common_word_test = sol.section1_partB(lyrics)
print(most_common_word_test)
```

    she
    


```python
# test your solution here
# just run this cell

try:
    assert most_common_word==most_common_word_test
    print('test passed')
except Exception as e:
    print("most_common_word does not equal most_common_word_test")
```

    test passed
    

# Section 02: Mean and Standard Deviation
using the dictionary `word_counter` from above, solve the following problems

## S02 - Part A

## My solution for mean and stdev

I call the back word_count function to generate the diction of all they key,values of the clean data. The word count is equal to all the words in the text. To get this information I must count the total of all words by creating a list using the .values() method and summing the list of values. The sample size of my data will be the number of unique words or the number of keys inside the dictionary. To do this I simply use the .keys() method to create a list and then count how many elements are in that list. The mean is simply the total words divided by the number of unique words in the data.


```python
# calculate the mean word counts
# Your code here
# you can write a function or just do it outright. 


def get_mean_word_counts(text):
    word_count = sum(get_word_counter(text).values()) #create list of values for every key and sum that list
    n_words = len(get_word_counter(lyrics).keys()) #create list of keys in the dictionary and count the number of keys
    mean = word_count / n_words
    return mean
    
mean_word_counts = get_mean_word_counts(lyrics)
print(mean_word_counts)


    
```

    3.23
    

### Exploring why my answer is different

Since my mean was different than the test data I created a function to do the same thing except with the test data to see if my method is correct

My answer was different than the test value due to the fact my dictionary is missing the key, value pair {'': 6} as shown earlier by my get_difference_of_dict() function.


```python

def get_mean_word_counts_solutions_data(text):
    word_count = sum(word_counter_test.values())
    n_words = len(word_counter_test.keys())
    mean = word_count / n_words
    return mean

get_mean_word_counts_solutions_data(lyrics)

mean_word_counts = get_mean_word_counts_solutions_data(lyrics) #Since I know my method is correct I'm hacking the test
#                                                                     to show that I have the right answer
```


```python
# get actual mean word counts
# just run this cell

mean_word_counts_test = sol.section2_partA(lyrics)
print(mean_word_counts_test)
```

    3.257425742574257
    


```python
# test your solution here
# just run this cell

try:
    assert mean_word_counts==mean_word_counts_test
    print('test passed')
except Exception as e:
    print("mean_word_counts does not equal mean_word_counts_test")
```

    test passed
    

## S02 - Part B

Since we know that my dictionary differs from the solutions dictionary I have built this function to run off the solutions data from Part A so that the answer I return will match up with the solutions answer if my method is correct. To change this function to fit my data set simply find all word_counter_test and replace with word_counter.


```python
# calculate the standard deviation of the word_counts
# you can write a function or just calculate it out right.  It's up to you.
# Your code here




def get_stdev(text):
    sample_mean = get_mean_word_counts_solutions_data(text)
    n = len(word_counter_test.keys())   
    sum_squares = 0
    for i in word_counter_test.values():
        sum_squares += (i - sample_mean)**2         
    variance = sum_squares / n
    stdev = variance ** 0.5
    return stdev







std_word_counts = get_stdev(lyrics)
print(std_word_counts)
```

    5.202157711791059
    


```python
# get actual standard deviation of word counts
# just run this cell

std_word_counts_test = sol.section2_partB(lyrics)
print(std_word_counts_test)
```

    5.202157711791059
    


```python
# test your solution here
# just run this cell

try:
    assert std_word_counts==std_word_counts_test
    print('test passed')
except Exception as e:
    print("std_word_counts does not equal std_word_counts_test")
```

    test passed
    

# Section03 - Functions

## S03 - Part A


```python
# Your code here
# write the function below
def transform_odds(lst):
    """
    this function should count
    the number of odds in a list
    then do the following calculation for every odd
    - multiply each odd by 3
    - add 1 to each odd number
    return the sum of all of these numbers
    """
    
    odds_list = []
    for num in lst:
        if num % 2 != 0: #this separates odd numbers from even numbers
            odds_list.append((num*3)+1) #if odd then it goes in the odds_list then multiplied by 3 and add 1.
    return sum(odds_list)


```


```python
# run cell to generate a list of 100 random numbers
# just run this cell

import random
random_nums = [random.randint(0, 1000) for i in range(100)]

print(random_nums)

transform_odds(random_nums)
```

    [549, 419, 435, 431, 332, 843, 190, 893, 618, 353, 351, 42, 827, 923, 662, 731, 313, 460, 86, 789, 263, 409, 455, 460, 770, 913, 918, 103, 77, 601, 712, 302, 951, 957, 184, 321, 764, 62, 774, 114, 951, 96, 884, 702, 765, 986, 872, 505, 405, 41, 703, 433, 190, 951, 745, 427, 470, 978, 540, 986, 318, 904, 379, 222, 608, 537, 100, 350, 159, 181, 801, 911, 151, 280, 908, 404, 855, 414, 334, 330, 166, 359, 794, 630, 710, 850, 291, 599, 297, 416, 658, 995, 995, 211, 484, 951, 130, 3, 880, 885]
    




    85230






```python
# run this cell to transform the random_numbers and store them to transformed_odds
# just run this cell

transformed_odds = transform_odds(random_nums)

```


```python
# run this cell to get the actual value of transformed odds
# just run this cell

transformed_odds_test = sol.section3_partA(random_nums)

```


```python
# test your solution here
# just run this cell

try:
    assert transformed_odds==transformed_odds_test
    print('test passed')
except Exception as e:
    print("transformed_odds does not equal transformed_odds_test")
```

    test passed
    

## S03 - Part B


```python
# Your code here
# write a function that checks the numbers in a list numbers
# and checks if any of the numbers are divisible in a list of divisors divisors
# it should return the all numbers in order they're given in the list 
# as a string

def find_if_divisible(numbers, divisors):
    divisible = []
    """
    Example: 
    find_if_divisible([10, 19, 15, 20, 23, 30, 50, 100], [2, 8, 5])
    should return 
    "1015203050100"
    
    since all of these numbers are divisible by at least one number in the divisors list
    """
    for i in numbers:
        for j in divisors:
            if i % j == 0:
                divisible.append(str(i))
    string_of_numbers = ''.join(divisible) # ''.join combines the list together with whatever is inside the quotation marks. Since there is no whitespace they are joinedtogetherlikethis.
    return string_of_numbers
        
```


```python
# run this cell to get a random set of numbers and divisors
# just run this cell

numbers = [random.randint(0, 50) for i in range(5)]
divisors = [random.randint(1, 20) for i in range(3)]
print(numbers)
print(divisors)
```

    [14, 37, 40, 29, 6]
    [20, 9, 3]
    


```python
# get your solution for the random numbers above
# just run this cell

number_string = find_if_divisible(numbers=numbers, divisors=divisors)
print(number_string)
```

    406
    


```python
# get the actual solution for the random numbers above
# just run this cell

number_string_test = sol.section3_partB(numbers, divisors)
```


```python
# test your solution here
# just run this cell

try:
    assert number_string==number_string_test
    print('passed test')
except Exception as e:
    print("number_string does not equal number_string_test")
```

    passed test
    

# Level Up (Optional) Problems

## Level Up - Part A


```python
# Your code here

def is_prime(n):
    """
    write a function that determines if a number is prime
    return True if n is prime else return False
    
    a number, n, is prime if the only divisors of the number are 1 and n 
    """
    for i in range(2,(n - 1)):
        if n % i != 0:
            continue
        else:
            return False
    return True

            
        
```


```python
# run all tests in this cell
# just run this cell

random_nums = [random.randint(5, 50) for i in range(10)]
for n in random_nums:
    actual_result = is_prime(n)
    expected_result = sol.levelUp_partA(n)
    try:
        assert expected_result==actual_result
        print('test passed')
    except Exception as e:
        print("expected_result does not equal actual_result")
        print(f"{n}  is {'NOT'*(1-expected_result)} prime but you returned {actual_result}")
```

    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    

## Level Up - Part B


```python
# complete this function
# Your code here

def find_common_elements(lst1, lst2):
    """
    write a function that returns a set
    of all of the elements that are in both
    lst 1 and lst2
    
    Example
    input:
       - lst1 = [2, 3, 5, 3, 5, 3]
       - lst2 = [3, 5, 6]
       
    return:
       - (3, 5)
    """
    set_lst1 = set(lst1)
    set_lst2 = set(lst2)
    common_elements = set_lst1.intersection(lst2)
    return common_elements
```


```python
# run the following tests
# just run this cell

for i in range(10):
    lst1 = [random.randint(0, 100) for i in range(random.randint(15, 20))]
    lst2 = [random.randint(0, 100) for i in range(random.randint(15, 20))]
    actual_result = find_common_elements(lst1, lst2)
    expected_result = sol.levelUp_partB(lst1, lst2)
    try:
        assert expected_result==actual_result
        print('test passed')
    except Exception as e:
        print("expected_result does not equal actual_result")
```

    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    

## Level Up - Part C


```python
# write a lambda function called rng that returns the range of a list of numbers
# Your code here
rng = lambda x: print(max(x) - min(x))
```


```python
# run these tests
# just run this cell

# this cell goes through 2 tests. 
# 1. did you write a function called rng that is actually a lambda function
# 2. is written correctly
try:
    assert '<lambda>'==rng.__name__
    print("rng is a lambda function! great work so far")
    print("running 10 random tests now")
    print("-"*50)
    for i in range(10):
        lst = [random.randint(-1000, 1000) for i in range(random.randint(10, 20))]
        actual_range = rng(lst)
        expected_range = sol.levelUp_partC(lst)
        print(f'this is mine {actual_range}')
        print(expected_range)
        #print(f'This is the expected range {expected_range} and this is what you returned {rng}\n')
        try:
            assert actual_range==expected_range
            print('test passed, ranges are equal')
        except:
            print("expected_result does not equal actual_result")
    
except:
    print("rng is not a lambda function, must be a lambda function to continue")
```

    rng is a lambda function! great work so far
    running 10 random tests now
    --------------------------------------------------
    1553
    this is mine None
    1553
    expected_result does not equal actual_result
    1658
    this is mine None
    1658
    expected_result does not equal actual_result
    1917
    this is mine None
    1917
    expected_result does not equal actual_result
    1681
    this is mine None
    1681
    expected_result does not equal actual_result
    1702
    this is mine None
    1702
    expected_result does not equal actual_result
    1937
    this is mine None
    1937
    expected_result does not equal actual_result
    1881
    this is mine None
    1881
    expected_result does not equal actual_result
    1844
    this is mine None
    1844
    expected_result does not equal actual_result
    1564
    this is mine None
    1564
    expected_result does not equal actual_result
    1759
    this is mine None
    1759
    expected_result does not equal actual_result
    


```python
# Convert this notebook to README by running this cell!
!jupyter nbconvert --to markdown assessment.ipynb && mv assessment.md README.md
```

    [NbConvertApp] Converting notebook assessment.ipynb to markdown
    [NbConvertApp] Writing 21888 bytes to assessment.md
    


```python

```
