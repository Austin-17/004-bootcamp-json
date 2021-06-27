# Introduction

Scott is a boy who automatically transforms into a squirrel on some
nights for unexplained reasons. He visited doctor Van Helsing who
suggested that he keep track of all the things he does on a regular
basis in a journal so that he can identify which activity is most
correlated with the transformation.

The journal is saved as a file called [journal.json](journal.json)
which has multiple entries like this one for each day of the month for
3 months. A total of 92 entries.

    {
      "events": [
        "carrot",
        "exercise",
        "weekend"
      ],
      "squirrel": false
    }
    
This file was then submitted to the doctor who analysed it to find out
which event is most correlated (positively or negatively) with the
transformation into the squirrel.

# Mathematical background

[Correlation](https://en.wikipedia.org/wiki/Correlation_and_dependence)
is a mathematically calculated value that represents how related two
values are. Consider two variables `X` and `Y`. For simplicity, let's
assume that the variables can take on only two values (True and
False). The correlation (denoted by `corr(X,Y)`), can vary between -1
to +1. If it's -1, it means that the two variables are perfectly
negatively correlated meaning that if `X` is True, `Y` will be
False. If it's +1, they're perfectly positively correlated. If `X`
is True, `Y` will also True. If the correlation is `0`, it means that
if `X` is True, there's equal probability that `Y` can be True or
False. 


## Formula

The correlation is usually denoted by ϕ. 


      ϕ = (n₁₁ * n₀₀ - n₁₀ * n₀₁) / sqrt(n₁₊ * n₀₊ * n₊₁ * n₊₀)


Here, The subscripts of n indicate the values of the two variables whose
correlations we're calculating. Let's call them x and y.


     n₁₁ is the number of times x and y were both True
     n₀₀ is the number of times x and y were both False
     n₁₀ is the number of times x was True but y was False
     n₀₁ is the number of times x was False but y was True
     
     n₁₊ is the number of times x was True regardless of the value of y
     n₀₊ is the number of times x was False regardless of the value of y
     n₊₁ is the number of times y was True regardless of the value of x
     n₊₀ is the number of times y was False regardless of the value of x


### Example

Consider the value for the two variables `X` and `Y`. 

      | X | Y |
      |---+---|
      | T | T |
      | T | F |
      | T | T |
      | F | T |
      | F | T |
      | T | F |
      | F | F |


     n₁₁  - number of times X and Y were both True         2
     n₀₀  - number of times X and Y were both False        1
     n₁₀  - number of times X was True but Y was False     2
     n₀₁  - number of times X was False but Y was True     2
     
     n₁₊  - number of times X was True regardless of the value of Y       4
     n₀₊  - number of times X was False regardless of the value of Y      3
     n₊₁  - number of times Y was True regardless of the value of X       4
     n₊₀  - number of times Y was False regardless of the value of X      3


Calculating the correlation like so

      ϕ = (n₁₁ * n₀₀ - n₁₀ * n₀₁) / sqrt(n₁₊ * n₀₊ * n₊₁ * n₊₀)
        = (2 * 1 - 2 * 2) / sqrt(4*3*4*3)
        = (2 - 4) / sqrt(144)
        = -2 / 12
        = -0.1667
  
This means that there's a slight negative correlation. If `X` is
True there's a slight chance that `Y` is False. If `X` were a social
event like "festival coming up", and `Y` were an event like "supply of
clothes" reducing, then you can make a reasonable assumption that if
the festival is coming up, there's a slight chance of supply of
clothes reducing. This doesn't suggest that `X` causes `Y`
(correlation is not causation). It only suggests that they're
correlated. 


    

