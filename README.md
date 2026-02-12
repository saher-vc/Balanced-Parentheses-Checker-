# Balanced-Parentheses-Checker-
#c++#stack its a code to check if the parentheses are balanced in the equation. we use top, pop and push function
#include <iostream>
using namespace std;

#define SIZE 100

char stack[SIZE];
int top = -1;

// push
void push(char value)
{
    if (top == SIZE - 1)
    {
        cout << "Stack is overflow" << endl;
    }
    else
    {
        top++;
        stack[top] = value;
    }
}

// pop
char pop()
{
    if (top == -1)
    {
        cout << "Stack is underflow" << endl;
        return '\0';
    }
    else
    {
        char value = stack[top];
        top--;
        return value;
    }
}

// matching parentheses
int matching(char open, char close)
{
    if (open == '(' && close == ')')
        return 1;
    if (open == '{' && close == '}')
        return 1;
    if (open == '[' && close == ']')
        return 1;

    return 0;
}

// check empty
bool isempty()
{
    if (top == -1)
        return true;
    else
        return false;
}

int main()
{
    char exp[100];
    cout << "Enter the expression: ";
    cin >> exp;

    int i = 0;

    while (exp[i] != '\0')
    {
        char c = exp[i];

        // opening brackets
        if (c == '(' || c == '{' || c == '[')
        {
            push(c);
        }
        // closing brackets
        else if (c == ')' || c == '}' || c == ']')
        {
            if (isempty())
            {
                cout << "Not Balanced (Empty stack)" << endl;
                return 0;
            }

            char p = pop();

            if (!matching(p, c))   // Correct order
            {
                cout << "Not Balanced" << endl;
                return 0;
            }
        }

        i++;
    }

    // Final check
    if (isempty())
        cout << "Balanced" << endl;
    else
        cout << "Not Balanced" << endl;

    return 0;
}
