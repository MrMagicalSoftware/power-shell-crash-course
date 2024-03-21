# power-shell-crash-course






Per visualizzare la lista dei processi :



PowerShell is a more advanced version of the command prompt. It is used to execute external programs like ping or copy, and automate different system administration tasks which are not accessible from cmd.exe.

```
get-process

```

<img width="855" alt="Screenshot 2024-03-21 alle 10 23 07" src="https://github.com/MrMagicalSoftware/power-shell-crash-course/assets/98833112/ea717d46-a4c4-4cf5-8cff-004a0a05c195">
<img width="854" alt="Screenshot 2024-03-21 alle 10 24 16" src="https://github.com/MrMagicalSoftware/power-shell-crash-course/assets/98833112/8f34cad6-850d-489d-963a-fdb46f6e0075">


```
start-process powershell -verb runas

```


**Windows PowerShell ISE**


![Screenshot 2024-03-21 alle 10 32 46](https://github.com/MrMagicalSoftware/power-shell-crash-course/assets/98833112/f9c30e56-4ae2-41e5-a3ae-1ebe09ace149)



**hello word**
```

echo "welcome to power shell"

```

Svae the file with ps1 extensions.




**Enable PowerShell Scripts**


When we start the PowerShell in a computer system, the default execution policy does not allow us to execute or run the scripts. 

There are four different types of execution policy in PowerShell:



    Restricted: In this policy, no script is executed.<br>
    RemoteSigned: In this policy, only those scripts are run, which are downloaded from the Internet, and these<br> must be signed by the trusted publisher.<br>
    Unrestricted: All the scripts of Windows PowerShell are run.<br>
    AllSigned: Only those scripts can be run, which are signed by a trusted publisher.<br><br>

Because the default execution policy of Windows PowerShell is restricted, so we cannot run any script until we change it. First, we set the execution policy to Unrestricted to execute the scripts by using the following command. 


```
Set-ExecutionPolicy Unrestricted  
```



**commenti in powershell**


Single line comments are those comments in which you can type a hash symbol # at the beginning of each line.
Everything to the right of the hash symbol will be ignored. 
If you write the multiple lines in a script, you had to use the hash # symbol at the starting of each line.


Multiple line comment


<pre>

    <# Multiple line Comment.........  
    .........  
    ....................#>  
    Statement-1  
    Statement-2  
    Statement-N  


  
</pre>



# Variables


```
# Assigning a string to a variable
$name = "John"

# Assigning a number to a variable
$age = 30

# Assigning the result of an expression to a variable
$total = 10 * 5

# Using variables in a string
Write-Host "Hello, my name is $name and I am $age years old."

# Using variables in a calculation
$doubleAge = $age * 2
Write-Host "Double my age is $doubleAge."

# Using variables in a loop
for ($i = 1; $i -le 5; $i++) {
    Write-Host "Count: $i"
}

```


**Automatic Variables**


In PowerShell, there are several automatic variables that are predefined and maintained by PowerShell itself. These variables provide information about various aspects of the PowerShell environment and the current session. Here are some common automatic variables in PowerShell:

1. `$PSVersionTable` - Contains information about the PowerShell version being used.

2. `$Host` - Represents the current PowerShell host application.

3. `$PSCmdlet` - Represents the cmdlet currently being executed in a script or function.

4. `$MyInvocation` - Contains information about the current script or command.

5. `$PID` - Contains the process ID of the current PowerShell session.

6. `$PWD` - Represents the present working directory in the current PowerShell session.

7. `$HOME` - Represents the user's home directory.

8. `$Args` - Contains an array of the arguments passed to a script or function.

9. `$Error` - Contains the most recent error object.

10. `$True` and `$False` - Represent boolean true and false values, respectively.


These automatic variables provide useful information and context within PowerShell scripts and functions.


Here's an example demonstrating the use of some of these automatic variables:

```powershell
# Display PowerShell version information
Write-Host "PowerShell Version: $($PSVersionTable.PSVersion)"

# Display process ID of the current session
Write-Host "Process ID: $PID"

# Display present working directory
Write-Host "Present Working Directory: $PWD"

# Display user's home directory
Write-Host "User's Home Directory: $HOME"

# Display arguments passed to the script
Write-Host "Arguments passed to script: $($Args -join ', ')"

# Display the most recent error object
if ($Error) {
    Write-Host "Error Message: $($Error[0].Exception.Message)"
}
```

**Preference Variables**



In PowerShell, preference variables are a set of special variables that allow users to customize the behavior of the PowerShell environment. These variables control aspects such as error reporting, command behavior, and output formatting. Here are some common preference variables:

1. `$ErrorActionPreference` - Controls how PowerShell responds to non-terminating errors. Possible values include `"Continue"`, `"SilentlyContinue"`, `"Stop"`, `"Inquire"`, and `"Ignore"`.

2. `$VerbosePreference` - Determines the level of detail displayed in verbose messages. Possible values are `"SilentlyContinue"`, `"Continue"`, `"Inquire"`, and `"Ignore"`.

3. `$DebugPreference` - Controls the display of debug messages. Possible values are `"SilentlyContinue"`, `"Continue"`, `"Inquire"`, and `"Ignore"`.

4. `$WarningPreference` - Specifies how PowerShell handles warning messages. Possible values are `"SilentlyContinue"`, `"Continue"`, `"Inquire"`, and `"Ignore"`.

5. `$ConfirmPreference` - Determines how PowerShell handles confirmation prompts. Possible values are `"None"`, `"Low"`, `"Medium"`, and `"High"`.

6. `$WhatIfPreference` - Controls how PowerShell handles the `-WhatIf` common parameter. Possible values are `"SilentlyContinue"`, `"Continue"`, `"Inquire"`, and `"Ignore"`.

7. `$FormatEnumerationLimit` - Specifies the maximum number of enumeration objects displayed in the output. The default value is 4.

These preference variables can be set within a PowerShell session or persisted across sessions by adding them to your PowerShell profile script. They provide flexibility in tailoring the PowerShell environment to suit your needs and preferences.



Preference variables can be set and modified by the user to customize the behavior of PowerShell commands and scripts. Here's an example of how to use preference variables:

```powershell
# Set the ErrorActionPreference to Stop
$ErrorActionPreference = "Stop"

# Suppress verbose messages
$VerbosePreference = "SilentlyContinue"

# Enable debug messages
$DebugPreference = "Continue"

# Ignore warning messages
$WarningPreference = "Ignore"

# Prompt for confirmation for destructive actions
$ConfirmPreference = "High"
```


_________________________________________

# Strutture dati 



In PowerShell, arrays are ordered collections of elements that can store multiple values of different types. Arrays can be created manually or dynamically. 

### Creating Arrays Manually:

```powershell
# Create an array of strings
$fruits = @("Apple", "Banana", "Orange")

# Create an array of integers
$numbers = @(1, 2, 3, 4, 5)

# Create an array of mixed types
$mixed = @(1, "Two", 3.5, $true)
```

### Accessing Array Elements:

```powershell
# Access individual elements using index
Write-Host "First fruit: $($fruits[0])"

# Update an element
$fruits[1] = "Grapes"

# Add elements
$fruits += "Pineapple"

# Remove an element
$fruits -= "Orange"

# Display all elements
Write-Host "All fruits: $($fruits -join ', ')"
```

### Dynamic Array Creation:

```powershell
# Create an empty array
$dynamicArray = @()

# Add elements dynamically
$dynamicArray += "Item1"
$dynamicArray += "Item2"
$dynamicArray += "Item3"
```

### Array Methods and Properties:

```powershell
# Get the number of elements in the array
$fruitCount = $fruits.Count

# Check if an element exists in the array
$isApplePresent = $fruits -contains "Apple"

# Sort the array
$sortedFruits = $fruits | Sort-Object

# Reverse the array
$reversedFruits = $fruits | Sort-Object -Descending
```

### Multidimensional Arrays:

```powershell
# Create a 2D array
$matrix = @(
    @(1, 2, 3),
    @(4, 5, 6),
    @(7, 8, 9)
)

# Access elements in a 2D array
$element = $matrix[1][2] # Accessing the element at row 2, column 3
```


________________________________________________________________________



**hash table**



In PowerShell, a hash table is a data structure that stores key-value pairs. Each key in a hash table must be unique, and each key is associated with a specific value. Hash tables are also known as dictionaries or associative arrays in other programming languages. Here's how you can create and use a hash table in PowerShell:

### Creating a Hash Table:

```powershell
# Create an empty hash table
$hashTable = @{}

# Create a hash table with initial key-value pairs
$hashTable = @{
    "Name" = "John"
    "Age" = 30
    "City" = "New York"
}
```

### Accessing Values in a Hash Table:

```powershell
# Access values using keys
Write-Host "Name: $($hashTable['Name'])"
Write-Host "Age: $($hashTable['Age'])"
Write-Host "City: $($hashTable['City'])"
```

### Adding or Modifying Entries:

```powershell
# Add or update key-value pairs
$hashTable['Occupation'] = "Engineer"
$hashTable['Age'] = 35  # Update existing value
```

### Removing Entries:

```powershell
# Remove a key-value pair
$hashTable.Remove('City')
```

### Iterating Over a Hash Table:

```powershell
# Iterate over each key-value pair
foreach ($key in $hashTable.Keys) {
    Write-Host "$key: $($hashTable[$key])"
}
```

### Checking for Existence:

```powershell
# Check if a key exists
if ($hashTable.ContainsKey('Name')) {
    Write-Host "Name exists"
}

# Check if a value exists
if ($hashTable.ContainsValue('New York')) {
    Write-Host "New York exists"
}
```

Hash tables are commonly used in PowerShell for storing configuration settings, organizing data, or passing parameters to functions. They provide a flexible and efficient way to work with key-value pairs.



# Power shell operators



PowerShell supports various operators that allow you to perform operations such as arithmetic, comparison, assignment, logical operations, and more. Here's an overview of some of the most commonly used operators in PowerShell:

### Arithmetic Operators:
- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulus (remainder of division)
- `++` Increment
- `--` Decrement

```powershell
$a = 10
$b = 5

$result1 = $a + $b   # 10 + 5 = 15
$result2 = $a - $b   # 10 - 5 = 5
$result3 = $a * $b   # 10 * 5 = 50
$result4 = $a / $b   # 10 / 5 = 2
$result5 = $a % $b   # 10 % 5 = 0 (remainder)
```

### Comparison Operators:
- `-eq` Equal to
- `-ne` Not equal to
- `-gt` Greater than
- `-lt` Less than
- `-ge` Greater than or equal to
- `-le` Less than or equal to

```powershell
$x = 10
$y = 5

$result1 = $x -eq $y   # False
$result2 = $x -ne $y   # True
$result3 = $x -gt $y   # True
$result4 = $x -lt $y   # False
$result5 = $x -ge $y   # True
$result6 = $x -le $y   # False
```

### Assignment Operators:
- `=` Simple assignment
- `+=` Add and assign
- `-=` Subtract and assign
- `*=` Multiply and assign
- `/=` Divide and assign

```powershell
$a = 10
$a += 5   # Equivalent to: $a = $a + 5
$a -= 3   # Equivalent to: $a = $a - 3
$a *= 2   # Equivalent to: $a = $a * 2
$a /= 4   # Equivalent to: $a = $a / 4
```

### Logical Operators:
- `-and` Logical AND
- `-or` Logical OR
- `-not` Logical NOT
- `-xor` Logical XOR

```powershell
$condition1 = $true
$condition2 = $false

$result1 = $condition1 -and $condition2   # False
$result2 = $condition1 -or $condition2    # True
$result3 = -not $condition1               # False
$result4 = $condition1 -xor $condition2   # True
```

### String Concatenation Operator:
- `+` Concatenates two strings

```powershell
$string1 = "Hello"
$string2 = "World"

$result = $string1 + ", " + $string2   # "Hello, World"
```

________________________________________________


**Redirection Operators**


In PowerShell, redirection operators are used to control the input and output of commands. They allow you to redirect the output of a command to a file, to append output to an existing file, or to redirect input from a file to a command. 

These redirection operators provide flexibility in managing input and output streams in PowerShell. They are useful for saving command output to files, handling errors, and providing input to commands from files.


Here are the commonly used redirection operators:


### Output Redirection:
- `>` - Redirects output to a file, overwriting the existing content.
- `>>` - Redirects output to a file, appending it to the existing content.

```powershell
# Redirect output to a file
Get-Process > processes.txt

# Append output to an existing file
Get-Service >> services.txt
```

### Error Redirection:
- `2>` - Redirects error output to a file, overwriting the existing content.
- `2>>` - Redirects error output to a file, appending it to the existing content.

```powershell
# Redirect error output to a file
Get-Process NoSuchProcess 2> errors.txt

# Append error output to an existing file
Get-Service NoSuchService 2>> errors.txt
```

### Combined Output/Error Redirection:
- `*>&1` - Redirects both output and error output to the same destination.

```powershell
# Redirect both output and error output to a file
Get-Process NoSuchProcess *> output_and_errors.txt
```

### Input Redirection:
- `<` - Redirects input from a file to a command.

```powershell
# Redirect input from a file to a command
Get-Content < input.txt
```


________________________________________


**Split and Join Operators**


In PowerShell, there are no specific split and join operators like in some other programming languages. However, you can achieve splitting and joining of strings using various methods and operators available in PowerShell.

### Splitting Strings:
You can split a string into an array of substrings using the `Split()` method or the `-split` operator.

#### Using the `Split()` method:
```powershell
$string = "apple,banana,orange"
$fruitsArray = $string.Split(",")
```

#### Using the `-split` operator:
```powershell
$string = "apple,banana,orange"
$fruitsArray = $string -split ","
```

### Joining Strings:
You can join an array of strings into a single string using the `-join` operator or by using the `Join()` method.

#### Using the `-join` operator:
```powershell
$fruitsArray = "apple", "banana", "orange"
$fruitsString = $fruitsArray -join ","
```

#### Using the `Join()` method:
```powershell
$fruitsArray = "apple", "banana", "orange"
$fruitsString = $fruitsArray -join ","
```

### Examples:

#### Splitting a String:
```powershell
$string = "apple,banana,orange"
$fruitsArray = $string.Split(",")
foreach ($fruit in $fruitsArray) {
    Write-Host $fruit
}
```

#### Joining Strings:
```powershell
$fruitsArray = "apple", "banana", "orange"
$fruitsString = $fruitsArray -join ","
Write-Host $fruitsString
```

These methods allow you to split strings into arrays and join arrays into strings, giving you flexibility in manipulating and processing text data in PowerShell.


___________________________________________________



# if statements




In PowerShell, the `if` statement is used for conditional branching, allowing you to execute specific blocks of code based on whether a condition evaluates to true or false. Here's the basic syntax of an `if` statement:

```powershell
if (condition) {
    # Code block to execute if the condition is true
}
```

If you need to handle both the true and false cases, you can also use the `else` statement:

```powershell
if (condition) {
    # Code block to execute if the condition is true
} else {
    # Code block to execute if the condition is false
}
```

Here's an example demonstrating the use of `if` and `else` statements:

```powershell
# Define a variable
$age = 25

# Check if the age is greater than or equal to 18
if ($age -ge 18) {
    Write-Host "You are an adult."
} else {
    Write-Host "You are a minor."
}
```

You can also use additional `elseif` statements to handle multiple conditions:

```powershell
# Define a variable
$score = 75

# Check the score range
if ($score -ge 90) {
    Write-Host "Grade: A"
} elseif ($score -ge 80) {
    Write-Host "Grade: B"
} elseif ($score -ge 70) {
    Write-Host "Grade: C"
} elseif ($score -ge 60) {
    Write-Host "Grade: D"
} else {
    Write-Host "Grade: F"
}
```

In PowerShell, conditions can be anything that evaluates to either true or false. Commonly used comparison operators like `-eq`, `-ne`, `-lt`, `-le`, `-gt`, and `-ge` are used to create conditions.

```powershell
# Define variables
$number1 = 10
$number2 = 20

# Check if number1 is less than number2
if ($number1 -lt $number2) {
    Write-Host "number1 is less than number2"
}
```

You can also use logical operators such as `-and`, `-or`, and `-not` to combine conditions:

```powershell
# Define variables
$age = 25
$isStudent = $true

# Check if the person is a student and under 18
if ($isStudent -and $age -lt 18) {
    Write-Host "The person is a student and under 18"
}
```



___________________________________________________

# Loops



In PowerShell, loops allow you to execute a block of code repeatedly until a certain condition is met. There are different types of loops available in PowerShell, including `for`, `foreach`, `while`, and `do...while`. Here's a brief overview of each:

1. **for Loop**: This loop is used when you know the number of iterations in advance.

```powershell
for ($i = 1; $i -le 5; $i++) {
    Write-Output "Iteration $i"
}
```

2. **foreach Loop**: This loop is used to iterate through each item in an array or collection.

```powershell
$colors = "red", "green", "blue"

foreach ($color in $colors) {
    Write-Output $color
}
```

3. **while Loop**: This loop executes a block of code as long as a specified condition is true.

```powershell
$i = 1

while ($i -le 5) {
    Write-Output "Iteration $i"
    $i++
}
```

4. **do...while Loop**: This loop is similar to the `while` loop, but it always executes the code block at least once before checking the condition.

```powershell
$i = 1

do {
    Write-Output "Iteration $i"
    $i++
} while ($i -le 5)
```

__________________________________________


# Functions





### Defining a Function:

```powershell
function MyFunction {
    # Function code goes here
    Write-Output "This is my function"
}
```

You can also define functions with parameters:

```powershell
function Greet {
    param (
        [string] $Name
    )
    Write-Output "Hello, $Name!"
}
```

### Calling a Function:

Once you've defined a function, you can call it by simply using its name followed by parentheses:

```powershell
MyFunction
```

For functions with parameters, you need to pass values when calling the function:

```powershell
Greet -Name "John"
```

### Returning Values:

Functions can return values using the `return` keyword or by simply outputting values using `Write-Output`:

```powershell
function Add {
    param (
        [int] $a,
        [int] $b
    )
    return ($a + $b)
}

$result = Add -a 5 -b 3
Write-Output "Result: $result"
```

### Advanced Function Features:

PowerShell also supports advanced function features such as parameter sets, pipeline input, and validation attributes. Here's an example:

```powershell
function Get-User {
    [CmdletBinding()]
    param (
        [Parameter(Position = 0, Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string] $Username,

        [Parameter(Position = 1)]
        [string] $Domain = "Contoso"
    )

    process {
        $fullUsername = "$Domain\$Username"
        Write-Output "Retrieving information for user: $fullUsername"
        # Code to retrieve user information
    }
}
```














