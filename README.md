# EEE 254
This repository contains codes developed algorithmically to reinforce the understanding of computer architecture(the way a computer thinks and processes), using the most efficient way to get the best performance  and the art of programming.
---



## Binary Search (Bisection Method)
``` python

user_num= int(input('Enter the nuber you want to find the cube root of'))
def find_cube_root (number, epsilon=0.01):
    start_time= time.time()
    steps = 0
    #since cube root of a negative number is negative, we search within negative range of the number, the same approach to the positive number. If number is 0, high and low are set to 0 [1 is the least positive number and -1 the highest negative number]
    low = min(-1, number) if number < 0 else 0
    high = max(1, number) if number > 0 else 0
    #the low,high is the valid interval that contains cube root
    guess = (high + low) / 2.0  #bisection

    while abs(guess ** 3 - number) > epsilon:
        if guess ** 3 < number:
        #set low to guess since evaluating for values below guess will cube to something smaller which can be eliminated
            low = guess
        else:
        #set high to guess since evaluating for values above guess willl cube to something bigger which can be eliminated
            high = guess
        guess = (high + low) / 2.0
        steps += 1
    end_time= time.time()
    total_time= end_time - start_time

    return guess, steps, total_time
 ```

```python
# Calling defined function and printing required output
cube_root, number_of_steps, time_taken=find_cube_root(user_num)
print(f"The estimated cube root of {user_num} is {cube_root}")
print(f"The number of steps taken: {steps}")
print(f"Time taken: {time_taken}"
```

```python
#To plot a graph, one or more points are required depending on user's decision
#Define a function to take care of number of points to be plotted on performance evaluation graph
def evaluate_performance:
     #declare an open list to contain values
      numbers = []
      #using a boolean to check state of number                                                                
        while True:
        try:
            count = int(input("How many numbers do you want to evaluate (minimum 1)? "))
            if count >= 1:# 
                break
            else:
                print("Please enter at least one number.")
        except ValueError:
            print("Invalid input. Please enter an integer.")
```

``` python
for i in range(count):
        while True:
            try:
                num = int(input(f"Enter number {i+1}: "))
                numbers.append(num)
                break
            except ValueError:
                print("Invalid input. Please enter an integer.")

    # Collect data for plotting
    x_labels = []  # Number of digits in each input
    y_labels = []  # Steps taken for estimation

    for num in numbers:
        root, steps = find_cube_root(num)
        x_labels.append(len(str(abs(num))))
        y_labels.append(steps)
        print(f"Cube root of {num} ≈ {root} (steps: {steps})")

    # Plotting the graph
    plt.plot(x_labels, y_labels, 'bo--')
    plt.title('Cube Root Estimation Steps vs Number Length')
    plt.xlabel('Number of Digits in Input')
    plt.ylabel('Steps Taken to Estimate Cube Root')
    plt.grid(True)
    plt.show()
```
