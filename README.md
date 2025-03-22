# Experiment-2
Write a program in Python language for Matrix multiplication fails. Introspect the causes for its failure and write down the possible reasons for its failure. 
## Aim
Write a python program for matrix multiplication and inspect for failures. 

## Algorithm
1.	Start the program.
2. Create empty list formatrix1, matrix2 and result.
3. Get the rows and columns count from the user.
4. Get the values of two matrix.
5. Perform matrix multiplication and store the answer in result.
6. Stop the program. 

## Program
```

r1, c1 = input("Enter row and column count for matrix 1: ").split()
r2, c2 = input("Enter row and column count for matrix 2: ").split()


matrix1 = []
matrix2 = []
result = []


if r1.isnumeric() and c1.isnumeric() and r2.isnumeric() and c2.isnumeric():
    r1, c1, r2, c2 = map(int, (r1, c1, r2, c2))

    
    if c1 != r2:
        print("Matrix multiplication not possible")
    elif max(r1, c1, r2, c2) > 20 or min(r1, c1, r2, c2) == 0:
        print("Matrix multiplication not possible")
    else:
      
        print("Enter elements for matrix 1:")
        for i in range(r1):
            row = []
            for j in range(c1):
                row.append(int(input(f"Matrix 1[{i+1}][{j+1}]: ")))
            matrix1.append(row)

      
        print("Enter elements for matrix 2:")
        for i in range(r2):
            row = []
            for j in range(c2):
                row.append(int(input(f"Matrix 2[{i+1}][{j+1}]: ")))
            matrix2.append(row)

        for i in range(r1):
            row = []
            for j in range(c2):
                total = 0
                for k in range(c1):
                    total += matrix1[i][k] * matrix2[k][j]
                row.append(total)
            result.append(row)

     
        print("\nResultant Matrix:")
        for row in result:
            print(" ".join(map(str, row)))
else:
    print("Enter valid numbers")
```


## Output
![Screenshot 2025-03-22 105749](https://github.com/user-attachments/assets/1fe0de44-cceb-4c0d-b43b-87f5b5b78cae)
![Screenshot 2025-03-22 110028](https://github.com/user-attachments/assets/0415d9b7-d471-4e67-85bb-12529df86922)
![Screenshot 2025-03-22 110616](https://github.com/user-attachments/assets/75cc0b16-f7cb-48e0-b77b-f344601fb84a)
![Screenshot 2025-03-22 110658](https://github.com/user-attachments/assets/4cc0bb91-443f-44de-a79d-b1c526f51746)
![Screenshot 2025-03-22 110749](https://github.com/user-attachments/assets/adead162-bad0-4bee-b383-9fdb53456000)




## Result
Thus, the python program for matrix multiplication is implemented and the causes      for its failure is 
introspected successfully. 
