#include<stdio.h>
#include<string.h>
int main() 
{
   char str[100];
   printf("enter the string to be checked: ");
   scanf("%s",str);
   int length= strlen(str);
   if (str[0]==str[length-1]&&str[1]==str[length-2])
   {
      printf("Accepted");
   }
    else
	{
      printf("Rejected");
    return 0;
    }
}
