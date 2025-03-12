# Experiment-2
## Name:Sathish.B
## Reg No:212224040299
Write a program in C language for Matrix multiplication fails. Introspect the causes for its failure and write down the possible reasons for its failure.
## Aim
The aim of this program is to perform matrix multiplication, understand the causes for failure during its execution, and identify possible reasons for failure. Matrix multiplication is a binary operation that produces a matrix from two matrices. The number of columns in the first matrix must be equal to the number of rows in the second matrix for multiplication to be possible.

## Algorithm
1.	Input the dimensions of the matrices: First, input the number of rows and columns for both matrices.
2.	Check for multiplication compatibility: Ensure the number of columns of the first matrix is equal to the number of rows of the second matrix.
3.	Input matrix elements: Input the elements for both matrices.
4.	Perform matrix multiplication: For each element in the resultant matrix, sum the products of the corresponding row and column elements from the two matrices.
5.	Output the resulting matrix: Display the resultant matrix.

## Causes for Failure:
Matrix multiplication may fail for the following reasons:
1.	Incompatible matrix dimensions: If the number of columns in the first matrix does not equal the number of rows in the second matrix, the multiplication is not possible, leading to failure.
2.	Memory allocation issues: If matrices are too large and memory is insufficient to store them, the program may crash or behave unexpectedly.
3.	Incorrect input or initialization: Providing incorrect or invalid values (such as non-numeric input) can cause errors.
4.	Array index out-of-bounds errors: Incorrect handling of array indices can lead to accessing memory outside the allocated space.

## Program
```
#include <stdio.h>
#include <stdlib.h>

// Function to multiply two matrices
void multiplyMatrices(int **A, int **B, int **C, int rowA, int colA, int rowB, int colB) {
    if (colA != rowB) {
        printf("Matrix multiplication is not possible. Number of columns in Matrix A must equal number of rows in Matrix B.\n");
        return;
    }

    for (int i = 0; i < rowA; i++) {
        for (int j = 0; j < colB; j++) {
            C[i][j] = 0;  // Initialize the result matrix element to zero
            for (int k = 0; k < colA; k++) {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

// Function to input matrix elements
void inputMatrix(int **matrix, int rows, int cols) {
    printf("Enter elements of the matrix:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("Element [%d][%d]: ", i + 1, j + 1);
            scanf("%d", &matrix[i][j]);
        }
    }
}

// Function to print matrix
void printMatrix(int **matrix, int rows, int cols) {
    printf("Resultant Matrix:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
}

// Function to allocate memory for a matrix
int** allocateMatrix(int rows, int cols) {
    // Check if the matrix exceeds the maximum allowable size
    if (rows > 10 || cols > 10) {
        printf("Matrix dimensions exceed the allowed maximum size of 10x10.\n");
        exit(1);  // Exit if matrix dimensions exceed allowed size
    }

    int **matrix = (int **)malloc(rows * sizeof(int *));
    if (matrix == NULL) {
        printf("Memory allocation for matrix failed!\n");
        exit(1);  // Exit if memory allocation fails
    }

    for (int i = 0; i < rows; i++) {
        matrix[i] = (int *)malloc(cols * sizeof(int));
        if (matrix[i] == NULL) {
            printf("Memory allocation for row %d failed!\n", i);
            exit(1);  // Exit if memory allocation fails
        }
    }

    return matrix;
}

// Function to free memory allocated for the matrix
void freeMatrix(int **matrix, int rows) {
    for (int i = 0; i < rows; i++) {
        free(matrix[i]);
    }
    free(matrix);
}

int main() {
    int **A, **B, **C;
    int rowA, colA, rowB, colB;

    // Input dimensions of Matrix A
    printf("Enter the number of rows and columns for Matrix A: ");
    scanf("%d %d", &rowA, &colA);

    // Input dimensions of Matrix B
    printf("Enter the number of rows and columns for Matrix B: ");
    scanf("%d %d", &rowB, &colB);

    // Check if the matrix dimensions are within the allowed size
    if (rowA > 10 || colA > 10 || rowB > 10 || colB > 10) {
        printf("Matrix dimensions exceed the allowed maximum size of 10x10.\n");
        return 0;  // Exit the program if dimensions exceed allowed size
    }

    // Check for multiplication compatibility
    if (colA != rowB) {
        printf("Matrix multiplication is not possible. The number of columns in A must be equal to the number of rows in B.\n");
        return 0; // Exit the program if matrices are incompatible
    }

    // Allocate memory for Matrix A
    A = allocateMatrix(rowA, colA);

    // Allocate memory for Matrix B
    B = allocateMatrix(rowB, colB);

    // Allocate memory for the result Matrix C
    C = allocateMatrix(rowA, colB);

    // Input elements for Matrix A
    inputMatrix(A, rowA, colA);

    // Input elements for Matrix B
    inputMatrix(B, rowB, colB);

    // Perform matrix multiplication
    multiplyMatrices(A, B, C, rowA, colA, rowB, colB);

    // Print the resulting matrix
    printMatrix(C, rowA, colB);

    // Free allocated memory for Matrix A, B, and C
    freeMatrix(A, rowA);
    freeMatrix(B, rowB);
    freeMatrix(C, rowA);

    return 0;
}
```
## Output

## Result
