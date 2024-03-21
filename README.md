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
















