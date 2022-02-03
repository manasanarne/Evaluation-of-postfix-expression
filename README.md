# Evaluation-of-postfix-expression
#include<stdio.h>
#include<ctype.h>
#include<math.h>
#define MAX 20
int a[MAX],top=-1;
int operation(int op1,int op2,char c)
{
    switch(c)
    {
        case '^': return(pow(op1,op2));
        case '*':return(op1*op2);
        case '+':return(op1+op2);
        case '-':return(op1-op2);
        case '/':return(op1/op2);
        case '%':return(op1%op2);

    }
}
void push(int x)
{
    if(top==MAX-1)
    {
        printf("The stack is overflown\n");
    }
    else
    {
        a[++top]=x;
    }
}
int pop()
{
    return a[top--];
}
void main()
{
    char postfix[MAX],c;
    int op1,op2,result,i=0;
    printf("\n Enter the postfix expression: ");
    scanf("%s",postfix);
    while(postfix[i]!='\0')
    {
        c=postfix[i];
        if(isdigit(c))
        {
            push(c-'0');
        }
        else
        {
            op2=pop();
            op1=pop();
            result=operation(op1,op2,c);
            push(result);
        }
        i++;
    }
    printf("The result of postfix expression is %d",a[top]);
}


OUTPUT:

 Enter the postfix expression: 632-5*+
The result of postfix expression is 11
