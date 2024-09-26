```mermaid
---
config:
  layout: elk
  theme: dark
---
flowchart TB
  Start[/Start/] ---> First
  First[[Computer finds a random integer between 0 and 100, inclusive. Assigns the value to 'x']]-->DoubleCheck
  DoubleCheck[[Computer checks that the value selected is within the predetermined range]] -->|Yes|Initally
  DoubleCheck -->|No|First
  Initally[Computer prompts user to enter an integer between 0 and 100]---
  UserInput(User provides input) -->FirstError
    subgraph Checks for Valid Input
    Reprompt{{Computer prompts user to enter a new integer}} -->UserInput
    FirstError[Is the value entered an integer?] --->|Yes| SecondError
    SecondError[Is the value entered >= 0 and <= 100?] --->|Yes| MoveOn([Continue])
    
    FirstError -->|No| Reprompt
    SecondError -->|No| Reprompt
    end

    subgraph Evaluates User Input
    MoveOn --- Compare[[User input is compared with random integer decided by the computer]]

    Compare --> Higher[Is the value entered higher than x?]
    Higher -->|No| Lower[Is the value entered lower than x?]
    Lower -->|No| EqualTo[Is the value entered equal to x?]
    

    end
    Higher -->|Yes| HigherOutput{{Console output informs the user their number is too high}} ----> Reprompt
    Lower -->|Yes| LowerOutput{{Console output informs the user their number is too low}} ----> Reprompt
    EqualTo -->|Yes| EndMessage{{Console output informs user their guess was correct.}}-->EndProgram
    EndProgram[/Program terminates/]
```
# Summary
##### This is a program where the computer selects a random integer between a specified range, in this example the specified range is between 0 and 100. 
##### The computer will prompt the user to guess integers within that range.
##### Program will end once the user's input is equal to the number selected by the computer.
# Description  
### *Step 1*  
* The computer will select a random number between 0 and 100.
* The program will assign this value to the variable **_x_**

### *Step 2*  
* The user will be prompted to input an integer between the 0 and 100.

### *Step 3*
* The program will evaluate whether or not the user's input was valid.  
  If the input provided by the user is:
  * Not numeric
  * Not within the specified range  
* The program will prompt the user to input a new value and will return to the beginning of **_Step 3_**
* If the input provided by the user is evaluated to be numeric and within the specified range, the program will move on to **_Step 4_**

### *Step 4*  
* In **_Step 4_**, the program will evaluate if the number is higher, lower, or equal to the value selected by the computer at the beginning of the program, which has been stored in the variable **_x_**.
* If the value is higher or lower than **_x_**, there will be a message stating as such, and the program will return to **_Step 3_**, prompting the user to enter a new value.
* If the value is equivalent to the **_x_**, there will be a message stating as such, and the program will terminate.
