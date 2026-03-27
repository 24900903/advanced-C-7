# advanced-C-7

EXP NO:1 C PROGRAM FOR ARRAY OF STRUCTURE TO CHECK ELIGIBILITY FOR THE VACCINE.

Aim: To write a C program for array of structure to check eligibility for the vaccine person age above 6 years of age.

Algorithm:

Declare structure eligible with age (integer) and n (character array)
Declare variable e of type eligible
Input age and name using scanf, store in e
If e.age <= 6
Print "Vaccine Eligibility: No" Else
Print "Vaccine Eligibility: Yes"
Print details (e.age, e.n)
Return 0
Program:
```
#include <stdio.h>

struct eligible {
    int age;
    char n[50];
};

int main() {
    struct eligible e;
    scanf("%s", e.n);
    scanf("%d", &e.age);

    if (e.age <= 6)
        printf("Vaccine Eligibility: No\n");
    else
        printf("Vaccine Eligibility: Yes\n");

    printf("Name: %s\nAge: %d\n", e.n, e.age);

    return 0;
}
```

Output:

<img width="351" height="245" alt="image" src="https://github.com/user-attachments/assets/c31f49f0-a5e3-4edb-ab66-c83d5f218558" />

Result: Thus, the program is verified successfully.

EXP NO:2 C PROGRAM FOR PASSING STRUCTURES AS FUNCTION ARGUMENTS AND RETURNING A STRUCTURE FROM A FUNCTION Aim: To write a C program for passing structure as function and returning a structure from a function

Algorithm:

Define structure numbers with members a and b.
Declare variable n of type numbers.
Prompt the user to enter values for a and b.
Input values for a and b into n using scanf.
Call the add function with n as an argument.
Print the result returned by the add function.
Return 0
Program:
```
#include <stdio.h>

struct numbers {
    int a, b;
};

struct numbers add(struct numbers n) {
    struct numbers result;
    result.a = n.a + n.b;
    return result;
}

int main() {
    struct numbers n, sum;

    printf("Enter two numbers: ");
    scanf("%d %d", &n.a, &n.b);

    sum = add(n);

    printf("Sum: %d\n", sum.a);

    return 0;
}
```

Output:

<img width="325" height="156" alt="image" src="https://github.com/user-attachments/assets/4effb892-8328-4d93-becf-6671249a2a75" />

Result: Thus, the program is verified successfully

EXP.NO:3 C PROGRAM TO READ A FILE NAME FROM USER AND WRITE THAT FILE USING FOPEN()

Aim: To write a C program to read a file name from user

Algorithm:

Include the necessary header file stdio.h.
Begin the main function.
Declare a file pointer p. Declare a character array name to store the file name.
Prompt the user to enter a file name. Use scanf to input the file name into the name array.
Print a message indicating that the file with the specified name has been created successfully.
Use fopen to open a file with the name provided by the user in write mode ("w").
If successful, continue to the next step.
If unsuccessful, print an error message and exit the program with a non-zero status.
Print a message indicating that the file has been opened successfully.
Use fclose to close the file.
Print a message indicating that the file has been closed.
End the main function.
Return 0 to indicate successful program execution.
Program:
```
#include <stdio.h>

int main() {
    FILE *p;
    char name[100];

    printf("Enter the file name: ");
    scanf("%s", name);

    p = fopen(name, "w");

    if (p == NULL) {
        printf("Error creating file.\n");
        return 1;
    }

    printf("File '%s' created successfully.\n", name);

    fclose(p);
    printf("File closed successfully.\n");

    return 0;
}
```

Output:

<img width="555" height="118" alt="image" src="https://github.com/user-attachments/assets/769e47e0-1ce7-40c5-871b-8d82f1e1020e" />


Result: Thus, the program is verified successfully

EXP NO:4 PROGRAM TO READ A FILE NAME FROM USER, WRITE THAT FILE AND INSERT TEXT IN TO THAT FILE Aim: To write a C program to read, a file and insert text in that file Algorithm:

Include the necessary header file stdio.h.
Begin the main function.
Declare a file pointer p. Declare character arrays name and text. Declare an integer variable num.
Prompt the user to enter a file name and the number of strings. Use scanf to input the file name into the name array and the number of strings into the num variable.
Use fopen to open a file with the name provided by the user in write mode ("w").
If successful, continue to the next step.
If unsuccessful, print an error message and exit the program with a non-zero status.
Print a message indicating that the file has been opened successfully.
Use a loop to input strings from the user and write them to the file using fputs.
Use fclose to close the file.
Print a message indicating that data has been added successfully.
End the main function.
Return 0 to indicate successful program execution.
Program:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char filename[100], text[1000];
    FILE *file;

    printf("Enter filename: ");
    scanf("%99s", filename);

    file = fopen(filename, "w+");
    if (!file) {
        perror("File error");
        return 1;
    }

    printf("Enter text: ");
    fgets(text, sizeof(text), stdin);
    text[strcspn(text, "\n")] = 0;
    fprintf(file, "%s\n", text);

    fprintf(file, "Appended text.\n");

    rewind(file);
    printf("\nFile contents:\n");
    char ch;
    while ((ch = fgetc(file)) != EOF)
        putchar(ch);
    printf("\n");

    fclose(file);
    return 0;
}
```


Output:

<img width="365" height="185" alt="image" src="https://github.com/user-attachments/assets/a9dfe15c-af4e-4af0-ae5d-82a77a0702b5" />


Result: Thus, the program is verified successfully

Ex No 5 : C PROGRAM TO DISPLAY STUDENT DETAILS USING STRUCTURE

Aim: The aim of this program is to dynamically allocate memory to store information about multiple subjects (name and marks), input the details for each subject, and then display the stored information. Finally, it frees the allocated memory to prevent memory leaks.

Algorithm: 1.Input the number of subjects.

2.Read the integer value n from the user, which represents the number of subjects.

3.Dynamically allocate memory:

4.Use malloc to allocate memory for n subjects. Each subject has a name (array of characters) and marks (integer).

5.If memory allocation fails (i.e., the pointer s is NULL), display an error message and exit the program.

6.Input the details of each subject

7.Use a for loop to read the name and marks of each subject using scanf. For each subject, store the name as a string and marks as an integer in the dynamically allocated memory.

8.Display the details of each subject

9.Use another for loop to print the name and marks of each subject.

10.Free the allocated memory

11.After all operations are done, call free(s) to release the dynamically allocated memory.

12.Return from the main function

13.End the program by returning 0.

Program:
```
#include <stdio.h>
struct Student {
    char name[50];
    int roll;
    float marks;
};

int main() {
    struct Student s;
    printf("Enter student name: ");
    fgets(s.name, sizeof(s.name), stdin);

    printf("Enter roll number: ");
    scanf("%d", &s.roll);

    printf("Enter marks: ");
    scanf("%f", &s.marks);
    printf("\n--- Student Details ---\n");
    printf("Name       : %s", s.name);
    printf("Roll No.   : %d\n", s.roll);
    printf("Marks      : %.2f\n", s.marks);

    return 0;
}
```

Output:

<img width="450" height="293" alt="image" src="https://github.com/user-attachments/assets/a8642fd2-8113-44b0-a493-e441aa047775" />

Result: Thus, the program is verified successfully
