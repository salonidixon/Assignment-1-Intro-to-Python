# Assignment-2-Intro-to-Python
## Name: Saloni Dixon 
## Programming Language: Python
## Date: 09/21/23 
### Description 
For this assignment, a python script was created in order to independently perform a series of tasks for the purpose of the familiarity of handling biological sequence data, competency and experience using fundamental commands in base Python, and appropriately managing a Git repository. This was completed utilizing scripts from multiple different languages, namely Python. 

### Required Files: 

chr1_GL383518v1_alt.fa enables 

### Required Packages: 
There are no specific packages required for this repository. 

### Execution: 
1. Wrote a Python program to read the complete sequence from chr1_GL383518v1_alt.fa.
#
    with open("OneDrive/Desktop/INFO-B 473/Assignment #2/chr1_GL383518v1_alt.fa", 'r') as file:
      # read all lines
      data = file.readlines()
    
      # initialize the empty string & store DNA sequence
      sequence = ""
    
      # concatenate DNA sequence lines into one continuous string & convert to uppercase 
      # to ensure consistency
      for i in data[1:-1]:
          sequence += i.strip()
          sequence = sequence.upper()

2. The 10th and 758th letter of the sequence are printed.

       # print the 10th letter of this sequence
       print('10th Letter of Sequence:', sequence[9])

       # print the 758th letter of this sequence
       print('10th Letter of Sequence:', sequence[757])

3. Wrote a Python program to create the reverse complement of the encoded DNA molecule mentioned above.
# 
      def reverse_complement(sequence_1):
        # creating a dictionary to store all base pair mappings
        base_pairs = {'A':'T', 'T':'A', 'C':'G', 'G':'C'}
    
        # reversing the DNA sequence
        reversed_seq = sequence[::-1]
    
        # generating reverse complement sequence
        reverse_complement_seq = ''.join(base_pairs[base] for base in reversed_seq)
    
        return reverse_complement_seq.strip()

     result = reverse_complement(sequence.upper())

4. The 79th & 500th-800th letter of the sequence are printed. 

       # print the 79th letter of this sequence
       print('79th Letter of Sequence:', result[78])

       # print the 500th through the 800th letters of this sequence
       print('500th-800th Letter of Sequence:', result[499:800 + 1])

5.  Wrote a python program that asks the user for a number, and generates a list of numbers that contains that many terms of the fibonacci numbers.

    def generate_fibonacci(n):
        fibonacci_sequence = []

        # initialize the first two terms of the Fibonacci sequence
        a, b = 0, 1

        for _ in range(n):
           fibonacci_sequence.append(a)
           a, b = b, a + b  # update the next Fibonacci numbers

     return fibonacci_sequence

7. Used generated list of Fibonacci numbers to make a second list of numbers, where the first number is 1, and each subsequent number is quotient of the corresponding fibonacci number and the previous fibonacci number.

def generate_quotient_list(fibonacci_sequence):
    quotient_list = [1]  # Initialize with the first number as 1

    for i in range(1, len(fibonacci_sequence)):
        # Calculate the quotient of the current Fibonacci number and the previous Fibonacci number
        quotient = fibonacci_sequence[i] / fibonacci_sequence[i - 1]
        quotient_list.append(quotient)

    return quotient_list

7. Used second list of numbers to make a third group of numbers, where the first two elements are 0, and each subsequence element is the difference of the corresponding element in the second list and the previous element in the list group. 

    def generate_difference_list(quotient_list):
    difference_list = [0, 0]  # Initialize with the first two elements as 0

    for i in range(2, len(quotient_list)):
        # Calculate the difference between the current quotient and the previous element in the difference list
        difference = quotient_list[i] - difference_list[i - 1]
        difference_list.append(difference)

    return difference_list

try:
    # Get the number of Fibonacci terms from the user
    n = int(input("Enter the number of Fibonacci numbers: "))

    if n <= 0:
        print("Please enter a positive integer!")
    else:
        # Generate the Fibonacci sequence
        fibonacci_sequence = generate_fibonacci(n)

        # Generate the quotient list
        quotient_list = generate_quotient_list(fibonacci_sequence)

        # Generate the difference list
        difference_list = generate_difference_list(quotient_list)

        # Print the generated sequences
        print("Fibonacci Sequence:") 
        print (fibonacci_sequence)

        print("\nQuotient List:")
        print (quotient_list)

        print("\nDifference List:") 
        print (difference_list)

except ValueError:
    print("Invalid input. Please enter a valid positive integer.")

8. Wrote a python program that uses nested loops to create a 10 by 10 matrix from nested lists that contains consecutive odd numbers starting at 1.

       # initialize the 10x10 matrix with consecutive odd numbers
       matrix = [[0] * 10 for _ in range(10)]
       current_value = 1

for i in range(10):
    for j in range(10):
        matrix[i][j] = current_value
        current_value += 2

    # calculate the trace of the matrix
    trace = sum(matrix[i][i] for i in range(10))

    # calculate the sum of upper triangle elements
    upper_triangle_sum = sum(matrix[i][j] for i in range(10) for j in range(i, 10))

    # calculate the sum of lower triangle elements
    lower_triangle_sum = sum(matrix[i][j] for i in range(10) for j in range(i + 1))

    # Display the matrix
    print("Your 10x10 matrix:")
    for row in matrix:
      print(row)

    # print the trace of matrix
    print(f"The trace of your matrix is {trace}.")

    # print sum of upper triangle elements
    print(f"The sum of upper triangular elements in your matrix is {upper_triangle_sum}.")

    # print sum of lower triangle elements
    print(f"The sum of lower triangular elements in your matrix is {lower_triangle_sum}.")

10. Wrote a Python program to read the sequence used in part 1 and creating a nested dictionary that contains the number of times each letter appears in the downloaded sequence, as a function of which kilobase of the sequence you are looking at.

        # defining the size of kilobase
        kb_size = 1000

        # initializing dictionary
        seq_counts = {}

for kb_start in range(0, len(sequence), kb_size):
      kb_end = kb_start + kb_size
      kb_sequence = sequence[kb_start:kb_end]

    # initialize a dictionary to count letter frequencies within this kb
    kb_counts = {'A': 0, 'T': 0, 'C': 0, 'G': 0}

    # count the occurrences of each letter in this kb sequence
    for letter in kb_sequence:
        if letter in kb_counts:
            kb_counts[letter] += 1

    # add the kb_counts dictionary to the nested dictionary
    seq_counts[f"KB {kb_start // kb_size + 1}"] = kb_counts

    # print nested dictionary
for kb, counts in seq_counts.items():
    print(f"Kilobase {kb}:")
    for base, count in counts.items():
        print(f"{base}: {count}")
