# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 


# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"

## COMMAND AND OUTPUT
```
mkdir my-folder
```
<img width="1469" height="43" alt="image" src="https://github.com/user-attachments/assets/aa99ab62-a6aa-47e7-bafd-3168838a9198" />


Remove the directory "my-folder"
## COMMAND AND OUTPUT
```
rmdir my-folder
```
<img width="1473" height="362" alt="Screenshot 2026-03-17 124437" src="https://github.com/user-attachments/assets/b1d0ee68-bd2a-43f0-8eca-f9d2c3e369e7" />



Create the file Rose.txt
## COMMAND AND OUTPUT
```
COPY CON Rose.txt
```
<img width="1901" height="113" alt="Screenshot 2026-03-17 124608" src="https://github.com/user-attachments/assets/9841ce00-7b9e-409b-90cb-a5473afd84f7" />


Create the file hello.txt using echo and redirection
## COMMAND AND OUTPUT
```
echo “hello world” > hello.txt
type hello.txt
```
<img width="1449" height="59" alt="Screenshot 2026-03-17 124713" src="https://github.com/user-attachments/assets/3dd1ff02-1256-4178-957f-71c6597f30dd" />



Copy the file hello.txt into the file hello1.txt
## COMMAND AND OUTPUT
```
copy hello.txt hello1.txt
```
<img width="1467" height="42" alt="Screenshot 2026-03-17 124832" src="https://github.com/user-attachments/assets/10e2153c-3cbb-4bbf-8c14-06cd8ceb98dc" />



Remove the file hello1.txt
## COMMAND AND OUTPUT
```
del hello1.txt
```
![alt text](../remove.png)


List out the file hello1.txt in the current directory
## COMMAND AND OUTPUT
```
dir hello1.txt
```
<img width="1467" height="172" alt="Screenshot 2026-03-17 124926" src="https://github.com/user-attachments/assets/30121e72-6b4d-404c-9202-645e089b6c27" />



List out all the associated file extensions 
## COMMAND AND OUTPUT
```
assoc | more
```
<img width="1442" height="650" alt="Screenshot 2026-03-17 125109" src="https://github.com/user-attachments/assets/4071a5bc-5b28-4755-9a19-d752152729ee" />



Compare the file hello.txt and rose.txt
## COMMAND AND OUTPUT
```
fc hello.txt Rose.txt
```
<img width="1447" height="188" alt="Screenshot 2026-03-17 125240" src="https://github.com/user-attachments/assets/53243422-49fc-4dfc-829b-827e17a72a16" />



## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".

## CODE
notepad 1.bat
```
@echo off
set name=John
echo Hello, %name%!
pause
```
1.bat

## OUTPUT

<img width="1471" height="77" alt="Screenshot 2026-03-17 125746" src="https://github.com/user-attachments/assets/e6fbf042-279b-4bec-b231-576aa1803134" />


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

## CODE
notepad 2.bat
```
@echo off
:main
set /p number=Enter a number: 
rem Calculate remainder when divided by 2
set /a remainder=%number% %% 2
if %remainder%==1 (
    echo %number% is an odd number.
) else (
    echo %number% is not an odd number.
)
:choice
set /p continue=Do you want to check another number? (Y/N): 
if /i "%continue%"=="Y" goto main
if /i "%continue%"=="N" goto end
echo Invalid choice, please enter Y or N.
goto choice
:end
echo Thank you for using the odd number checker!
pause
```
2.bat

## OUTPUT

<img width="1471" height="218" alt="Screenshot 2026-03-17 130215" src="https://github.com/user-attachments/assets/9ac96331-ddb8-40dc-99e4-eb1a6f7b0f04" />


Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

## CODE 
notepad 3.bat
```
@echo off
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause
```
3.bat

## OUTPUT

<img width="1459" height="173" alt="Screenshot 2026-03-17 130337" src="https://github.com/user-attachments/assets/15c756cc-4e5c-49ac-adff-57e22380363e" />



Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

## CODE
notepad 4.bat 
```
@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause
```
echo "hello world" > sample.txt

4.bat

## OUTPUT

<img width="1471" height="80" alt="Screenshot 2026-03-17 130806" src="https://github.com/user-attachments/assets/eac21f31-dc61-4f51-8fb2-3c819892c6e4" />



Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

## CODE 
notepad 5.bat

```
@echo off
:menu
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option: 
if "%choice%"=="1" goto hello
if "%choice%"=="2" goto createfile
if "%choice%"=="3" goto end

:hello
echo Hello, World!
goto menu

:createfile
echo Creating a file...
echo This is a new file > newfile.txt
goto menu
:end
echo Goodbye!
pause

```
5.bat

## OUTPUT

<img width="1475" height="402" alt="Screenshot 2026-03-17 131058" src="https://github.com/user-attachments/assets/800dd0f3-39e1-4c99-a336-76e7cd7d0c8f" />


# RESULT:
The commands/batch files are executed successfully.

