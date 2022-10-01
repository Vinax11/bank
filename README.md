# bank
#include<stdio.h>
#include<string.h>
 
 struct login
{
	char email1[100];
	
	char pass[100];
};


struct detail
{
	int pin_card_no[100];
	
	char name[100];
	
} acc_detail;


struct bank
{
	char amount[100];
	
}balance_detil;


void check_balance();
void deposite();
void withdraw();

main()
{   struct login l1;
    char ch;
    char u[50],p[50];
    char ch1;
   	

        
         FILE *fp;
         login:
         fp=fopen("login1.txt","a");
         
         printf("\t\t\t\t\t<<<<<*** Enter user ID ***>>>>>\n\t\t\t\t\tEnter Here :\t");
         scanf("%s",l1.email1);
         
         printf("\n\n\t\t\t\t\t<<<<<*** Enter password ***>>>>>\n\t\t\t\t\tEnter Here :\t");
         scanf("%s",l1.pass);
         
         fprintf(fp,"email=%s  password=%s",l1.email1,l1.pass);
         
         printf("\n\n\t\t\t\t\t<<<<<*** Ragister done ***>>>>>");
         
         fclose(fp);
         

         printf("\n\n\n\n\n\t\t\t\t\t<<<<<*** Login here ***>>>>>");
         
         
         printf("\n\n\n\t\t\t\t\t<<<<<*** Enter user id ***>>>>>\n\t\t\t\t\tEnter Here :\t");
         scanf("%s",u);
       
	     
         printf("\n\n\t\t\t\t\t<<<<<*** Enter password ***>>>>>\n\t\t\t\t\tEnter Here :\t");
         scanf("%s",p);
         
	
         FILE *fp1;
         
         fp=fopen("login.txt1","r");
         
         fscanf(fp,"%s%s",l1.email1,l1.pass);
         
         printf("%s%s",l1.email1,l1.pass);
                
         if(((strcmp(l1.email1,u)==0)&&(strcmp(l1.pass,p)==0)))
          {
            printf("\n\n\t\t\t\t\t<<<<<*** Login done ***>>>>>");
          }
         else
         {
          printf("\n\n\t\t\t\t\t<<<<<*** wrong login ***>>>>>");
          goto login;
         }
         fclose(fp);
          
			 printf("\n\n\t\t\t\t\t<<<<<*** DO YOU WANT TO LOGIN ANOTHER ACCOUNT ***>>>>>\n\t\t\t\t\tEnter here :\t");
            fflush(stdin);
			 scanf("%c",&ch1);
			 if((ch1=='y')||(ch1=='Y'))
			 {
			 	goto login;
			 }
		
		
		
		FILE *fp2;
		fp2=fopen("accountholder.txt","a");
		
		printf("\n\nEnter your name\nEnter here:\t");
		scanf("%s",acc_detail.name);
		
		printf("\n\nEnter your pin code\nEnter here:\t");
		scanf("%s",acc_detail.pin_card_no);		 
		
		fclose(fp2);
		
     	int no;
     	menu:
     	printf("\n\nSelect your choise by entering numbers");	
		printf("\n\n1...Deposite");	 
		printf("\n\n2...Check balance");
		printf("\n\n3...Withdraw");
		printf("\n\n4...exit\nEnter here\t");
		scanf("%d",&no);
		if(no==1)
		{
			  deposite();
			goto menu;
	    }	 
	    
	    else if(no==2)
	    {
	       check_balance();
		   goto menu;	
		}
		
		else if(no==3)
		{
			withdraw();
			goto menu;
		}
		else if(no==4)
		{
			
		}
		else 
		{
			printf("\nPlease enter valid numbers");
			goto menu;
		}
}

void deposite()
{  
   FILE *fp3;
   
   fp3=fopen("accoundetail.txt","a");
   
   printf("\n\nEnter amount you want to deposite\nEnter here:\t");
   fflush(stdin);
   scanf("%s",balance_detil.amount);
   printf("\n\n\nYour ammount %s deposite sucessfully",balance_detil.amount);
	fprintf(fp3,"%s",balance_detil.amount);
   fclose(fp3);
}

void check_balance()
{
	FILE *fp4;
   
   fp4=fopen("accoundetail.txt","r");
   
   printf("\n\nYour ammount %s",balance_detil.amount);
	
   fclose(fp4);
}

void withdraw()
{
	char no[100];
	
	printf("\n\n\n\nEnter amount to widhraw\nEnter here:\t");
	fflush(stdin);
	scanf("%s",no);
	
	FILE *fp5;
	
	fp5=fopen("accoundetail.txt","w");
	
	fscanf(fp5,"%s",balance_detil.amount);
	printf("%s",balance_detil.amount);
	
	if(strcmp(balance_detil.amount,no)==balance_detil.amount-no>=1000)
	{
		printf("\n\n\nWithdraw Succesfully");
		printf("\n\n\nCollect your cash");
	}
	else 
	{
		printf("\n\n\nBalance not sufficienty");
		printf("\n\nYou can see you bance here");
		check_balance();
		printf("\n\nYou cant withdraw you money");
	}
}
