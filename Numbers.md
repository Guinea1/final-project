# _Bobby's Site_ ![Icon](PageIcon.png)

[Home](README.md) | [About me](About.md) | [Turtle House](House.md) | [Recursive Turtle](Recursive.md) | [Random Number Reader/Writer](Numbers.md)

## Random Number Reader/Writer _(1040)_

![Python Icon](http://www.pngall.com/wp-content/uploads/2016/05/Python-Logo-PNG-Image.png)
###### [Image Source](http://www.pngall.com/)

Here is the code from my python (file) random number reader/writer program:

### randomread.py
```
# Create count variable
count = 0

# Try to open numbers file for reading
while(True):
    try:
        number_file = open('randomnum.txt', 'r')
    except OSError:
        input("An error occoured while opening randomnum.txt (does the file exist?), press enter to try again")
    else:
        break

# Print numbers in file
print('List of random numbers in randomnum.txt:')

for line in number_file:
    donotprint = False
    while(True):
        try:
            number = int(line)
            if(number <= 0):
                print("This line in randomnum.txt contains a number that is 0 or negative:", str(line))
                line = 1
                donotprint = True
                continue
        except ValueError:
            print("This line in randomnum.txt contains a value which is not a number:", str(line))
            line = 1
            donotprint = True
        else:
            break
    count += 1
    if(not donotprint):
        print(str(number))

#Print number count
print("\nRandom number count:", str(count))
```

### randomwrite.py
```
import random

# Open file
while(True):
    try:
        number_file = open("randomnum.txt", "w")
    except OSError:
        input("An error occoured while opening/creating the file randomnum.txt, press enter to try again")
    else:
        break

# Input values
while(True):
        try:
            quantity_numbers = int(input("How many random numbers should be generated: "))
            if(quantity_numbers <= 0):
                print("Quantity of numbers must be positive and not 0")
                continue
        except ValueError:
                print("Invalid value, only numbers are valid.")
        else:
                break

while(True):
        try:
            lowest_number = int(input("What should the lowest random number be: "))
            if(lowest_number <= 0):
                print("Lowest random number must be positive and not 0")
                continue
        except ValueError:
                print("Invalid value, only numbers are valid.")
        else:
                break

while(True):
        try:
            highest_number = int(input("What should the highest random number be: "))
            if(highest_number <= 0):
                print("Highest random number must be positive and not 0")
                continue
        except ValueError:
                print("Invalid value, only numbers are valid.")
        else:
                break

# Generate and write random numbers in range
for num in range(quantity_numbers):
        generated_number = random.randint(lowest_number, highest_number)
        while(True):
            try:
                number_file.write(str(generated_number) + "\n")
            except OSError:
                input("An error occoured while writing to the file randomnum.txt, press enter to try again")
            else:
                break

# Close the file and print finished
number_file.close()
print("The random numbers were written to randomnum.txt")
```
