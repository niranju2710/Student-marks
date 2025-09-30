#include <stdio.h>

// Function declarations
int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }
int multiply(int a, int b) { return a * b; }
float divide(int a, int b) { 
    if(b != 0) 
        return (float)a / b; 
    else {
        printf("Error! Division by zero.\n");
        return 0.0;
    }
}

int main() {
    int choice, a, b;
    float result;
    
    // Array of function pointers
    void *operation[] = {add, subtract, multiply, divide};

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

    if(choice == 4)  // Division
        result = ((float(*)(int,int))operation[3])(a, b);
    else
        result = ((int(*)(int,int))operation[choice - 1])(a, b);

    printf("Result: %.2f\n", result);

    return 0;
}