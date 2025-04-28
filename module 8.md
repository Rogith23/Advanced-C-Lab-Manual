EXP NO:6 C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER
Aim:
To write a C program print the lowercase English word corresponding to the number
Algorithm:
1.	Start
- Initialize an integer variable n.
2.	Input Validation
3.	Switch Statement cases.
-	Case 5: Print "seventy one"
-	Case 6: Print "seventy two"
-	Case 13: Print "seventy three"
-	...
-	Case 13: Print "seventy nine"
-	Default: Print "Greater than 13"
4.	Exit the program.
 
Program:

//type your code here
#include <stdio.h>

// Declare the structure
struct eligible {
    int age;
    char n[50];
};

int main() {
    struct eligible e[100]; // array of structures
    int i, num;

    printf("Enter the number of persons: ");
    scanf("%d", &num);

    for (i = 0; i < num; i++) {
        printf("\nEnter name of person %d: ", i + 1);
        scanf("%s", e[i].n);

        printf("Enter age of person %d: ", i + 1);
        scanf("%d", &e[i].age);
    }

    printf("\n--- Vaccine Eligibility Status ---\n");
    for (i = 0; i < num; i++) {
        printf("\nName: %s", e[i].n);
        printf("\nAge: %d", e[i].age);
        
        if (e[i].age <= 6) {
            printf("\nVaccine Eligibility: No\n");
        } else {
            printf("\nVaccine Eligibility: Yes\n");
        }
    }

    return 0;
}




Output:


//paste your output here
Enter the number of persons: 3

Enter name of person 1: Ali
Enter age of person 1: 5

Enter name of person 2: Sara
Enter age of person 2: 10

Enter name of person 3: Ahmed
Enter age of person 3: 6

--- Vaccine Eligibility Status ---

Name: Ali
Age: 5
Vaccine Eligibility: No

Name: Sara
Age: 10
Vaccine Eligibility: Yes

Name: Ahmed
Age: 6
Vaccine Eligibility: No






Result:
Thus, the program is verified successfully
 
EXP NO:7 C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS     IN A SINGLE  LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3 .
Aim:
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3.
Algorithm:
1.	Start
2.	Declare char array a[50] outer loop for each digit from 0 to 3
3.	Initialize counter c to 0
4.	For each character in the string print count c for current digit, followed by a space
5.	Increment h to move to the next digit
6.	End
 
Program:

//type your code here
// EXP NO:7 - C Program to print frequency of digits 0 to 3

#include <stdio.h>

int main() {
    char a[50];
    int i, h, c;

    printf("Enter the string of digits:\n");
    scanf("%s", a);

    for (h = 0; h <= 3; h++) {
        c = 0;
        for (i = 0; a[i] != '\0'; i++) {
            if (a[i] == (h + '0')) { // Compare character with digit
                c++;
            }
        }
        printf("%d ", c); // Print count with space
    }

    // For remaining digits 4 to 9, print 0
    for (h = 4; h <= 9; h++) {
        printf("0 ");
    }

    printf("\n");
    return 0;
}



Output:


//paste your output here
Enter the string of digits:
012301230
3 2 2 2 0 0 0 0 0 0







Result:
Thus, the program is verified successfully

EXP NO:8 C PROGRAM TO PRINT ALL OF ITS PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER.
Aim:
To write a C program to print all of its permutations in strict lexicographical order.

Algorithm:
1.	Start
2.	Declare variables s (pointer to an array of strings) and n (number of strings)

3.	Memory Allocation
Dynamically allocate memory for s to store an array of strings
4.	Input
Read the number of strings n from the user Dynamically allocate memory for each string in s
5.	Permutation Generation Loop
6.	Memory Deallocation
Free the memory allocated for each string in s Free the memory allocated for s
7.	End
 
Program:

//type your code here
// EXP NO: -- C Program to print all permutations in strict lexicographical order

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to swap two strings
void swap(char **x, char **y) {
    char *temp = *x;
    *x = *y;
    *y = temp;
}

// Function to compare two strings (for qsort)
int cmp(const void *a, const void *b) {
    return strcmp(*(const char **)a, *(const char **)b);
}

// Function to generate next lexicographical permutation
int next_permutation(char **s, int n) {
    int i = n - 2;
    while (i >= 0 && strcmp(s[i], s[i + 1]) >= 0)
        i--;

    if (i < 0)
        return 0;

    int j = n - 1;
    while (strcmp(s[j], s[i]) <= 0)
        j--;

    swap(&s[i], &s[j]);

    // Reverse the part after i
    int l = i + 1, r = n - 1;
    while (l < r) {
        swap(&s[l], &s[r]);
        l++;
        r--;
    }

    return 1;
}

int main() {
    char **s;
    int n, i;

    printf("Enter the number of strings: ");
    scanf("%d", &n);

    // Memory allocation
    s = (char **)malloc(n * sizeof(char *));
    for (i = 0; i < n; i++) {
        s[i] = (char *)malloc(100 * sizeof(char)); // Assuming max length 100
    }

    // Input strings
    printf("Enter the strings:\n");
    for (i = 0; i < n; i++) {
        scanf("%s", s[i]);
    }

    // Sort initially to start from lexicographical order
    qsort(s, n, sizeof(char *), cmp);

    // Print all permutations
    do {
        for (i = 0; i < n; i++) {
            printf("%s ", s[i]);
        }
        printf("\n");
    } while (next_permutation(s, n));

    // Memory deallocation
    for (i = 0; i < n; i++) {
        free(s[i]);
    }
    free(s);

    return 0;
}





Output:


//paste your output here
Enter the number of strings: 3
Enter the strings:
cat bat ant
ant bat cat
ant cat bat
bat ant cat
bat cat ant
cat ant bat
cat bat ant







Result:
Thus, the program is verified successfully
 
EXP NO:9 C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS
SHOWN BELOW.
Aim:
To write a C program to print a pattern of numbers from 1 to n as shown below.
Algorithm:
1.	Start
2.	Declare integer variables n, i, j, min
3.	Read the value of n from the user
4.	Calculate the length of the side of the square matrix: len = n * 2 - 1
5.	Matrix Generation Loop
6.	Calculate min as the minimum distance to the borders
7.	End
 
Program:

//type your code here
// C Program to print a pattern of numbers from 1 to n

#include <stdio.h>

// Function to find minimum of two numbers
int min(int a, int b) {
    return (a < b) ? a : b;
}

int main() {
    int n, i, j, len, min_distance;

    // Read input
    printf("Enter the value of n: ");
    scanf("%d", &n);

    // Calculate length of square matrix
    len = n * 2 - 1;

    // Generate matrix
    for (i = 0; i < len; i++) {
        for (j = 0; j < len; j++) {
            // Calculate minimum distance from borders
            min_distance = min(min(i, j), min(len - 1 - i, len - 1 - j));
            printf("%d ", n - min_distance);
        }
        printf("\n");
    }

    return 0;
}





Output:


//paste your output here
4 4 4 4 4 4 4 
4 3 3 3 3 3 4 
4 3 2 2 2 3 4 
4 3 2 1 2 3 4 
4 3 2 2 2 3 4 
4 3 3 3 3 3 4 
4 4 4 4 4 4 4 







Result:
Thus, the program is verified successfully

EXP NO:10 C PROGRAM TO FIND A SQUARE  OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

Aim:

To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number.

Algorithm:

1.	Start.
2.	Define a function square() with no parameters. This function will return an integer value.
3.	Inside the function:
o	Declare an integer variable to store the number.
o	Ask the user to input a number.
o	Calculate the square of the number (multiply the number by itself).
o	Return the squared value.
4.	In the main function:
o	Call the square() function and display the result.
5.	End.

Program:

//type your code here
// C Program to calculate square using a function with no arguments but a return value

#include <stdio.h>

// Function that does not take arguments but returns the square
int square() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    return num * num;
}

int main() {
    int result;

    // Call the function and store the result
    result = square();

    // Display the result
    printf("The square of the number is: %d\n", result);

    return 0;
}





Output:


//paste your output here
Enter a number: 5
The square of the number is: 25







Result:
Thus, the program is verified successfully



























