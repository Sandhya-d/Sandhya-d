//1.Write a C program to divide the integer array into two halves using function
//recursion. Call the user-defined “divide” function recursively, with the left half
//of the split array being passed as an argument for that function. Let the
//recursive function to get executed until the array size becomes one. Count the
//number of iterations to reach the base condition. Explain the working
//procedure of recursive function with stack structure
#include <stdio.h>
void divide(int arr[], int low, int high);
int main() {
   int arr[100], n, i;
   printf("Enter the size of the array: ");
   scanf("%d", &n);
   printf("Enter the elements of the array:\n");
   for (i = 0; i < n; i++) {
      scanf("%d", &arr[i]);
   }
   divide(arr, 0, n - 1);
   return 0;
}
void divide(int arr[], int low, int high) {
   static int count = 0;
   int mid
   if (low < high) {
      mid = (low + high) / 2;
      divide(arr, low, mid);
      divide(arr, mid + 1, high);
   }
   count++;
   if (low == high) {
      printf("The number of iterations to reach base condition is: %d\n", count);
   }
}

//2.Consider that you are going to analyze the characters in the given string. Write
//a C program to extract the characters in the given string and print whether the
//character is an uppercase alphabet, lowercase alphabet, digits, whitespace,
//special symbols. Print the count of each category by storing their counts in an
//array. Use appropriate looping constructs to implement this.
#include <stdio.h>
#include <ctype.h>

int main() {
    char str[100];
    int count[5] = {0}; // initialize count array to 0

    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin); // read string from user input

    for (int i = 0; str[i] != '\0'; i++) {
        if (isupper(str[i])) {
            count[0]++;
            printf("%c is an uppercase alphabet\n", str[i]);
        }
        else if (islower(str[i])) {
            count[1]++;
            printf("%c is a lowercase alphabet\n", str[i]);
        }
        else if (isdigit(str[i])) {
            count[2]++;
            printf("%c is a digit\n", str[i]);
        }
        else if (isspace(str[i])) {
            count[3]++;
            printf("%c is a whitespace character\n", str[i]);
        }
        else {
            count[4]++;
            printf("%c is a special symbol\n", str[i]);
        }
    }

    printf("Count of uppercase alphabets: %d\n", count[0]);
    printf("Count of lowercase alphabets: %d\n", count[1]);
    printf("Count of digits: %d\n", count[2]);
    printf("Count of whitespace characters: %d\n", count[3]);
    printf("Count of special symbols: %d\n", count[4]);

    return 0;
}

//3.Write a c program to find the sum of the series 1!/1+2!/2+3!/3+4!/4+5!/5 ... n!/n 
//by utilizing user defined recursive function? Get the value of n from the
//user. Do not use any storage classes. Without returning the calculated result
//from the function, display the result in main
#include <stdio.h>

double factorial(int n); // function prototype for recursive factorial function

int main() {
    int n;
    double sum = 0.0;

    printf("Enter a positive integer: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        sum += factorial(i) / i;
    }

    printf("Sum of the series is: %lf", sum);

    return 0;
}

// recursive function to calculate factorial
double factorial(int n) {
    if (n == 0 || n == 1) {
        return 1.0;
    }
    else {
        return n * factorial(n - 1);
    }
}

//4. ABC car showroom sells various types of cars such as Hatchback, Sedan,
//SUVs, and MUV. Due to the year-end sale, the showroom provides a 3%, 5%,
//10%, and 15% discount for various car models Hatchback, Sedan, SUV, and
//MUV respectively. Also applies 12% of GST for the total amount of purchase
//Write a C program to implement the above scenario which will read the
//type_of_the_car, price_of_the_car and extra-fitting_price_of_the_car as input
//from the user and estimate the Net amount to be paid to the showroom. If the
//type of car is other than Hatchback, Sedan, SUV, and MUV then display
//“Invalid Type”. (Difficulty Level: Easy)
//The net amount to be paid to the showroom is estimated as follows:
//(For example-if the purchased car is Hatchback)
//Total = price_of_the_car + extra-fitting_price_of_the_car
//Discount = Total * 0.03 // 0.03 denotes 3% wastage
//gst = (Total - Discount) * 0.12 // 0.12 denotes12% GST
//net = Total – Discount + gst
#include <stdio.h>

int main() {
    char carType[20];
    float carPrice, extraFittingPrice, total, discount, gst, net;

    // Prompt the user for input
    printf("Enter car type (Hatchback, Sedan, SUV, MUV): ");
    scanf("%s", carType);
    printf("Enter car price: ");
    scanf("%f", &carPrice);
    printf("Enter extra fitting price: ");
    scanf("%f", &extraFittingPrice);

    // Calculate the total amount
    total = carPrice + extraFittingPrice;

    // Calculate the discount based on the car type
    if (strcmp(carType, "Hatchback") == 0) {
        discount = total * 0.03;
    }
    else if (strcmp(carType, "Sedan") == 0) {
        discount = total * 0.05;
    }
    else if (strcmp(carType, "SUV") == 0) {
        discount = total * 0.1;
    }
    else if (strcmp(carType, "MUV") == 0) {
        discount = total * 0.15;
    }
    else {
        printf("Invalid Type\n");
        return 0;
    }

    // Calculate the GST and net amount
    gst = (total - discount) * 0.12;
    net = total - discount + gst;

    // Display the net amount to be paid
    printf("Net amount to be paid: %.2f\n", net);

    return 0;
}

//5.Write a C Program that reads the input as a string from the user in main (). 
//The input should be a sentence with two words. Pass this string to a function.
//Inside the function do the following operations:  For the first word, keep only the first character of the word to be in upper
//case and the rest of the characters in lower case.For the second word, convert all the characters into upper case letter.
//Print the revised string consisting of the two words in the function itself
//Find the length of the entire string. Print its length in the function itself in
//the next line of the revised string. Use appropriate string function to print
//this result in the next line. Return the length of the string, if the length is 
//less than 20. Else return the size of the string. 
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int process_string(char str[]);

int main() {
    char sentence[50];

    printf("Enter a sentence with two words: ");
    fgets(sentence, 50, stdin);

    int length = process_string(sentence);
    printf("Length of the string: %d\n", length);

    if (length < 20) {
        return length;
    } else {
        return sizeof(sentence);
    }
}

int process_string(char str[]) {
    char first_word[20], second_word[20];

    // extract the two words from the input sentence
    sscanf(str, "%s %s", first_word, second_word);

    // convert the first word to upper case
    first_word[0] = toupper(first_word[0]);
    for (int i = 1; i < strlen(first_word); i++) {
        first_word[i] = tolower(first_word[i]);
    }

    // convert the second word to upper case
    for (int i = 0; i < strlen(second_word); i++) {
        second_word[i] = toupper(second_word[i]);
    }

    // print the revised string consisting of the two words
    printf("%s %s\n", first_word, second_word);

    // return the length of the entire string
    return strlen(str);
}
//PAT1
#include <stdio.h>
#include <math.h>

int isPrime(int n);
int isArmstrong(int n);
int isPerfect(int n);

int main()
{
    int n;
    printf("Enter an integer: ");
    scanf("%d", &n);

    if (isPrime(n))
        printf("%d is a prime number\n", n);
    else
        printf("%d is not a prime number\n", n);

    if (isArmstrong(n))
        printf("%d is an Armstrong number\n", n);
    else
        printf("%d is not an Armstrong number\n", n);

    if (isPerfect(n))
        printf("%d is a perfect number\n", n);
    else
        printf("%d is not a perfect number\n", n);

    return 0;
}
int isPrime(int n)
{
    if (n <= 1)
        return 0;

    for (int i = 2; i <= sqrt(n); i++)
    {
        if (n % i == 0)
            return 0;
    }
    return 1;
}
int isArmstrong(int n)
{
    int sum = 0;
    int temp = n;
    int digits = 0;
    while (temp != 0)
    {
        digits++;
        temp /= 10;
    }
    temp = n;
    while (temp != 0)
    {
        int remainder = temp % 10;
        sum += pow(remainder, digits);
        temp /= 10;
    }
    return (sum == n);
}
int isPerfect(int n)
int sum = 0;
{
    for (int i = 1; i < n; i++)
    {
        if (n % i == 0)
            sum += i;
    }

    return (sum == n);
}
//PAT2
#include <stdio.h>
#include <ctype.h>

#define MAX_LEN 100

int main() {
    char str[MAX_LEN];
    int i, vowels, consonants, spaces, special, words;

    printf("Enter a string: ");
    fgets(str, MAX_LEN, stdin);

    i = vowels = consonants = spaces = special = words = 0;

    while (str[i] != '\0') {
        if (isalpha(str[i])) {
            if (str[i] == 'a' || str[i] == 'e' || str[i] == 'i' || str[i] == 'o' || str[i] == 'u' ||
                str[i] == 'A' || str[i] == 'E' || str[i] == 'I' || str[i] == 'O' || str[i] == 'U') {
                vowels++;
            } else {
                consonants++;
            }
        } else if (isspace(str[i])) {
            spaces++;
        } else if (ispunct(str[i])) {
            special++;
        }

        if (isspace(str[i]) || ispunct(str[i])) {
            words++;
        }

        i++;
    }

    // for cases when string is entered with newline character at the end
    if (str[i-1] == '\n') {
        words--;
    }

    printf("\nWords = %d\n", words+1);
    printf("Vowels = %d\n", vowels);
    printf("Consonants = %d\n", consonants);
    printf("Space = %d\n", spaces);
    printf("Special Characters = %d\n", special);

    return 0;
}
//CAT1a
#include <stdio.h>
#include <string.h>

#define MAX_LEN 100

int main() {
    char str[MAX_LEN];
    int len, i, j, freq, repeat_flag;
    char *first_non_repeated, *first_repeated;

    printf("Enter a string: ");
    fgets(str, MAX_LEN, stdin);

    len = strlen(str);
    // remove the newline character from the end of the string
    if (str[len-1] == '\n') {
        str[len-1] = '\0';
        len--;
    }

    printf("Length of the string is: %d\n", len);

    // count word frequency
    freq = 1;
    for (i = 0; i < len; i++) {
        if (str[i] == ' ') {
            freq++;
        }
    }
    printf("Word frequency is: %d\n", freq);

    // find first repeated character
    repeat_flag = 0;
    for (i = 0; i < len; i++) {
        for (j = i+1; j < len; j++) {
            if (str[i] == str[j]) {
                first_repeated = &str[i];
                repeat_flag = 1;
                break;
            }
        }
        if (repeat_flag == 1) {
            break;
        }
    }

    if (repeat_flag == 0) {
        printf("No repeated characters found in the string.\n");
    } else {
        printf("First repeated character is: %c\n", *first_repeated);
    }

    // find first non-repeated character
    for (i = 0; i < len; i++) {
        repeat_flag = 0;
        for (j = i+1; j < len; j++) {
            if (str[i] == str[j]) {
                repeat_flag = 1;
                break;
            }
        }
        if (repeat_flag == 0) {
            first_non_repeated = &str[i];
            break;
        }
    }

    printf("First non-repeated character is: %c\n", *first_non_repeated);

    return 0;
}
//CAT1b
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_EMPLOYEES 50

struct Employee {
    char name[50];
    int age;
    char position[50];
    char date_of_joining[11];
};

int compare_by_name(const void *a, const void *b) {
    const struct Employee *ea = (const struct Employee *)a;
    const struct Employee *eb = (const struct Employee *)b;
    return strcmp(ea->name, eb->name);
}

int compare_by_date_of_joining(const void *a, const void *b) {
    const struct Employee *ea = (const struct Employee *)a;
    const struct Employee *eb = (const struct Employee *)b;
    return strcmp(ea->date_of_joining, eb->date_of_joining);
}

int main() {
    int num_employees;
    printf("Enter the number of employees: ");
    scanf("%d", &num_employees);

    struct Employee employees[MAX_EMPLOYEES];
    for (int i = 0; i < num_employees; i++) {
        printf("Enter details of employee %d:\n", i+1);
        printf("Name: ");
        scanf("%s", employees[i].name);
        printf("Age: ");
        scanf("%d", &employees[i].age);
        printf("Position: ");
        scanf("%s", employees[i].position);
        printf("Date of joining (dd/mm/yyyy): ");
        scanf("%s", employees[i].date_of_joining);
    }

    // sort by name
    qsort(employees, num_employees, sizeof(struct Employee), compare_by_name);

    printf("\nEmployee List sorted by name:\n");
    for (int i = 0; i < num_employees; i++) {
        printf("Name: %s\n", employees[i].name);
        printf("Age: %d\n", employees[i].age);
        printf("Position: %s\n", employees[i].position);
        printf("Date of Joining: %s\n", employees[i].date_of_joining);
        printf("\n");
    }

    // sort by date of joining
    qsort(employees, num_employees, sizeof(struct Employee), compare_by_date_of_joining);

    printf("\nEmployee List sorted by date of joining:\n");
    for (int i = 0; i < num_employees; i++) {
        printf("Name: %s\n", employees[i].name);
        printf("Age: %d\n", employees[i].age);
        printf("Position: %s\n", employees[i].position);
        printf("Date of Joining: %s\n", employees[i].date_of_joining);
        printf("\n");
    }

    return 0;
}
//TRIANGLE PROBLEM
#include<stdio.h>

int main() {
    int i, j, a, b, c, count_acute = 0, count_right = 0, count_obtuse = 0, count_wrong = 0;
    for (i = 0; i < 5; i++) {
        printf("Enter the three angles of the triangle: ");
        scanf("%d%d%d", &a, &b, &c);
        if (a + b + c != 180) {
            printf("Wrong entry. Please try again.\n");
            count_wrong++;
            i--;
        } else {
            if (a < 90 && b < 90 && c < 90) {
                count_acute++;
            } else if (a == 90 || b == 90 || c == 90) {
                count_right++;
            } else {
                count_obtuse++;
            }
        }
    }
    printf("\nAcute Angled Triangle: %d\n", count_acute);
    printf("Right Angled Triangle: %d\n", count_right);
    printf("Obtuse Angled Triangle: %d\n", count_obtuse);
    printf("Wrong Entries: %d\n", count_wrong);
    return 0;
}
//G2 CAT
//qn.1
#include <stdio.h>

int main() {
    int chennai_temps[7], delhi_temps[7], haveri_temps[7], gangtok_temps[7];
    int i, chennai_temp, delhi_temp, haveri_temp, gangtok_temp;

    // Get temperatures of Chennai for the week
    printf("Enter the temperature of Chennai for the week:\n");
    for (i = 0; i < 7; i++) {
        scanf("%d", &chennai_temps[i]);
        // Validate temperature range
        if (chennai_temps[i] < 28 || chennai_temps[i] > 33) {
            printf("Temperature should be between 28C to 33C. Enter again.\n");
            i--;
        }
    }

    // Calculate temperatures of Delhi and Haveri for the week
    for (i = 0; i < 7; i++) {
        delhi_temps[i] = chennai_temps[i] - 8;
        haveri_temps[i] = chennai_temps[i] + 5;
    }

    // Calculate temperature of Gangtok for the week
    for (i = 0; i < 7; i++) {
        gangtok_temps[i] = haveri_temps[i] - delhi_temps[i];
    }

    // Print temperature of Gangtok for the week
    printf("\nTemperature of Gangtok for the week:\n");
    for (i = 0; i < 7; i++) {
        printf("%dC\n", gangtok_temps[i]);
    }

    return 0;
}

//Qn.2
#include <stdio.h>

// Function to calculate the sum of digits of a number
int sum_of_digits(int n) {
    int sum = 0;
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    return sum;
}

int main() {
    int sum = 0;

    // Calculating the sum of all even four-digit numbers
    for (int i = 1000; i < 10000; i += 2) {
        sum += i;
    }

    // Finding the single digit by repeatedly adding digits
    while (sum >= 10) {
        sum = sum_of_digits(sum);
    }

    // Checking if the single digit is odd or even
    if (sum % 2 == 0) {
        printf("Even found\n");
    } else {
        printf("Odd found\n");
    }

    return 0;
}
