# Student-marks
To calculate the total students marks
#include <stdio.h>

// Function declarations
int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }
int multiply(int a, int b) { return a * b; }
int divide(int a, int b) { 
    if(b != 0) 
        return a / b; 
    else {
        printf("Error! Division by zero.\n");
        return 0;
    }
}

int main() {
    int choice, a, b, result;
    
    // Array of function pointers
    int (*operation[])(int, int) = {add, subtract, multiply, divide};

    printf("Simple Calculator using Function Pointers\n");
    printf("1. Add\n2. Subtract\n3. Multiply\n4. Divide\n");
    printf("Enter your choice (1-4): ");
    scanf("%d", &choice);

    if(choice < 1 || choice > 4) {
        printf("Invalid choice!\n");
        return 0;
    }

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    // Call the chosen function through pointer
    result = operation[choice - 1](a, b);
    printf("Result: %d\n", result);

    return 0;
