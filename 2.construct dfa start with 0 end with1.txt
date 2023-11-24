#include<stdio.h>
#include<string.h>
int main() 
{
   char str[100];
   printf("enter the string to be checked: ");
   scanf("%s",str);
   int lenght = strlen(str);
   if(str[0] == '0' && str[lenght-1] == '1')
   {
      printf("Accepted");
   }
    else
	{
      printf("Rejected");
    return 0;
    }
}
