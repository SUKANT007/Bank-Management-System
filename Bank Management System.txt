#include<stdio.h>
#include<string.h>
#include<stdlib.h>
struct date
{
    int day;
    int month;
    int year;
};
struct details
{
    int account_no;
    char account_name[30];

    long int phone_no;
    //int type;
    int deposit;
    struct date dat;
    char gender[50];
    long int aadhar;
    char debit_issue[20];
    char emailid[100];
    char password[30];

}*person[50];
static int count=0;
void createAccount()
{
    int main_exit;
    system("COLOR 2");
    FILE *create;
    create=fopen("ss.txt","a+");
    system("cls");
    printf("\t\t\xB2\xB2\xB2\xB2\xB2\xB2\xB2  CREATE ACCOUNT  \xB2\xB2\xB2\xB2\xB2\xB2\xB2\n\n");
    person[count] =(struct details*)malloc(sizeof(struct details));
    printf("\tenter your name\n\t");
    fflush(stdin);
    scanf("%s", &person[count]->account_name);
    fflush(stdin);
    printf("\tenter account number\n\t");
    fflush(stdin);
    scanf("%d",&person[count]->account_no);
    fflush(stdin);
    printf("\tenter your gender\n\t");
    fflush(stdin);
    scanf("%s", &person[count]->gender);
    printf("\tenter phone number\n\t");
    fflush(stdin);
    scanf("%d",&person[count]->phone_no);
    printf("\tenter your txte of birth (dd/mm/yyyy): \n\t");
    fflush(stdin);
    scanf("%d/%d/%d",&person[count]->dat.day,&person[count]->dat.month,&person[count]->dat.year);
    printf("\tenter amount to be deposited\n\t");
    fflush(stdin);
    scanf("%d",&person[count]->deposit);
    int answer;
    printf("Press 1 if you want to link aadhar card now.\nPress 0 if you want to do it later\n");
    fflush(stdin);
    scanf("%d", &answer);
    person[count]->aadhar = 0;
    if (answer)
    {
        printf("Enter aadhar card number\n");
        scanf("%d", &person[count]->aadhar);
    }
    strcpy(person[count]->debit_issue,"NO");
    printf("Enter email id\n");
    fflush(stdin);
    scanf("%s", person[count]->emailid);
    printf("Set your password\n");
    fflush(stdin);
    scanf("%s", person[count]->password);
    fprintf(create,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",person[count]->account_no,person[count]->account_name,person[count]->phone_no,person[count]->deposit,person[count]->dat.day,person[count]->dat.month,person[count]->dat.year,person[count]->gender,person[count]->aadhar,person[count]->debit_issue,person[count]->emailid,person[count]->password);
   // printf("enter type of account\n");
    //printf("press 1 for YES\n 2 for No\n");
    /*printf("ENTER 1 FOR SAVING \n ENTER 2 FOR CURRENT\n ENTER 3 FOR FIXED\n");
    scanf("%d",&type);
    if(type==1)
    {

    }*/
count += 1;
fclose(create);

 printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();
}
void display_account()
{   int main_exit;
    FILE *display;
    display=fopen("ss.txt","r");
    system("cls");
    int flag = 0;
    int accNumb;
    char pass[100];
    printf("Enter account number\n");
    scanf("%d", &accNumb);
    if(display==NULL)
        printf("heyyyyy");
    for(int i = 0; i < count; i++)
        {
            fscanf(display,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

            flag = 1;
            printf("Enter password\n");
            scanf("%s",pass);
           // printf("%d",strcmp(pass,person[i]->password));
            if(strcmp(pass,person[i]->password) == 0)
            {

               printf("account found\n");
               printf("ACCOUNT NAME-%28s\n",person[i]->account_name);
               printf("ACCOUNT NUMBER-%26d\n",person[i]->account_no);
               printf("AMOUNT DEPOSITED-%24d\n",person[i]->deposit);
               printf("GENDER-%34s\n",person[i]->gender);
               printf("datE OF BIRTH-%25d/%d/%d\n",person[i]->dat.day,person[i]->dat.month,person[i]->dat.year);
               printf("AADHAR CARD NUMBER-%22d\n",person[i]->aadhar);
               printf("DEBIT CARD ISSUED%23s\n",person[i]->debit_issue);
               printf("PHONE NUMBER-%28d\n",person[i]->phone_no);
               printf("EMAIL ID-%32s\n",person[i]->emailid);

            }
            else
            {
                printf("WRONG PASSWORD\n");
            }

        }
        }
    if(!flag)
        {
            printf("No such account found.\n");
        }
        fclose(display);

        printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();
}




void fordelay(int j)
{   int i,k;
    for(i=0;i<j;i++)
         k=i;
}

void withdraw()
{
    int main_exit;
    FILE *old,*new1;
    old=fopen("ss.txt","r");
    new1=fopen("new1.txt","w");
    system("cls");
   int wdraw;
   int flag=0;
   int accNumb;
   char pass[20];
   printf("Enter account number\n");
   scanf("%d", &accNumb);
    for(int i = 0; i < count; i++)

        {
         fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

            flag = 1;
            printf("Enter password\n");
            scanf("%s",pass);
           // printf("%d",strcmp(pass,person[i]->password));
            if(strcmp(pass,person[i]->password) == 0)
            {
                printf("ENTER AMOUNT TO BE WITHDRAW\n");
                scanf("%d",&wdraw);
                person[i]->deposit=person[i]->deposit-wdraw;
                printf("AMOUNT WITHDRAWN SUCCESSFULLY\n");
               fprintf(new1,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            }
            else
            {
                printf("WRONG PASSWORD!");
            }
           }




}
    if(!flag)
        {
            printf("ACCOUNT NOT FOUND!\n");
        }
        fclose(old);
        fclose(new1);
        remove("ss.txt");
        rename("new1.txt","ss.txt");

        printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();
}
void transfer()
{
    int main_exit;
    FILE *old,*new1;
    old=fopen("ss.txt","r");
    new1=fopen("new1.txt","w");
    system("cls");
    int transfr;
   int flag=0;
   int flag1 = 0;
   int accNumb;
   char pass[20];
   int transACC;
   int i;
   int j;
   printf("Enter account number of the account you want to transfer your money in:\n");
   scanf("%d", &transACC);
   for(j = 0;j<count; j++)
   {
       fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",person[j]->account_no,person[j]->account_name,person[j]->phone_no,person[j]->deposit,person[j]->dat.day,person[j]->dat.month,person[j]->dat.year,person[j]->gender,person[j]->aadhar,person[j]->debit_issue,person[j]->emailid,person[j]->password);
       if(person[j]->account_no == transACC)
        {
        flag1 = 1;
        break;
        }
   }
   if(!flag1)
   {
       printf("No such account found\n");
       return;
   }

    printf("Enter your account number\n");
   scanf("%d", &accNumb);
    for(i = 0; i < count; i++)

        {
            fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",person[i]->account_no,person[i]->account_name,person[i]->phone_no,person[i]->deposit,person[i]->dat.day,person[i]->dat.month,person[i]->dat.year,person[i]->gender,person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

            flag = 1;
            printf("Enter password\n");
            scanf("%s",pass);
           // printf("%d",strcmp(pass,person[i]->password));
            if(strcmp(pass,person[i]->password) == 0)
            {
                printf("ENTER AMOUNT TO BE TRANSFERRED\n");
                scanf("%d",&transfr);
                printf("AMOUNT TRANSFERRED SUCCESSFULLY\n");
                person[i]->deposit=person[i]->deposit-transfr;
                person[j]->deposit += transfr;
                fprintf(new1,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            }
            else
            {
                printf("WRONG PASSWORD!");
            }
           }
        }
        if(!flag)
        {
            printf("ACCOUNT NOT FOUND!\n");
        }
        fclose(old);
        fclose(new1);
        remove("ss.dat");
        rename("new1.txt","ss.txt");


        printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();

}

void deposit()
{
    int main_exit;
    FILE *old,*new1;
    old=fopen("ss.txt","r");
    new1=fopen("new1.txt","w");
    system("cls");
    int dposit;

    int flag=0;
   int accNumb;
   char pass[20];
   printf("Enter account number\n");
   scanf("%d", &accNumb);
    for(int i = 0; i < count; i++)

        {
            fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

            flag = 1;
            printf("Enter password\n");
            scanf("%s",pass);
           // printf("%d",strcmp(pass,person[i]->password));
            if(strcmp(pass,person[i]->password) == 0)
            {
               printf("ENTER AMOUNT TO BE DEPOSITED\n");
                scanf("%d",&dposit);
                person[i]->deposit=person[i]->deposit+dposit;
                printf("AMOUNT DEPOSITED SUCCESSFULLY\n");
               fprintf(new1,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);

            }
            else
            {
                printf("WRONG PASSWORD!\n");
            }
           }


        }
        if(!flag)
        {
            printf("ACCOUNT NOT FOUND!\n");
        }
        fclose(old);
        fclose(new1);
        remove("ss.txt");
        rename("new1.txt","ss.txt");
        printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();


}
void debit_card()
{
    int main_exit;
    FILE *old,*new1;
    old=fopen("ss.txt","r");
    new1=fopen("new1.txt","w");
    system("cls");
    int flag=0;
   int accNumb;
   char pass[20];
   printf("Enter account number\n");
   scanf("%d", &accNumb);
    for(int i = 0; i < count; i++)

        {
            fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

                flag = 1;
                printf("Enter password\n");
                scanf("%s",pass);
               // printf("%d",strcmp(pass,person[i]->password));
                if(strcmp(pass,person[i]->password) == 0)
                {
                   strcpy(person[i]->debit_issue,"YES");
                   printf("YOUR DEBIT CARD ISSUED\n");

                   fprintf(new1,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
                }
                else
                {
                    printf("WRONG PASSWORD!\n");
                }
           }

        }
        if(!flag)
        {
            printf("ACCOUNT NOT FOUND!\n");
        }

        fclose(old);
        fclose(new1);
        remove("ss.txt");
        rename("new1.txt","ss.txt");
        printf("\nEnter 1 to go to the main menu and 0 to exit:");
        scanf("%d",&main_exit);
        system("cls");
        if (main_exit==1)
            menu();
        else
            close();
}

void transaction()
{

   system("cls");
   int choice;
    printf(" WHAT YOU WANT TO DO?\n ");
    printf(" 1.DEPOSIT \n 2. WITHDRAW\n 3. TRANSFER\n");
    scanf("%d",&choice);
    switch(choice)
    {
        case 1:
        {

            deposit();
            break;
        }
        case 2:
            {
                withdraw();
                break;
            }
        case 3:
            {
                transfer();
                break;
            }
    }

}
void aadhar_set()
{
    int main_exit;
    FILE *old,*new1;
    old=fopen("ss.txt","r");
    new1=fopen("new1.txt","w");
    system("cls");
    int flag=0;
    int accNumb;
    char pass[20];
    printf("Enter account number\n");
    scanf("%d", &accNumb);
    for(int i=0;i<count;i++)

        {
            fscanf(old,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            if(person[i]->account_no == accNumb)
           {

            flag = 1;
            printf("Enter password\n");
            scanf("%s",pass);
           // printf("%d",strcmp(pass,person[i]->password));
            if(strcmp(pass,person[i]->password) == 0)
            {
               printf("Enter your aadhar card number:\n");
               scanf("%d", &person[i]->aadhar);
               printf("your aadhar card linked successfully\n");
               fprintf(new1,"%d %s %ld %d %d/%d/%d %s %ld %s %s %s\n",&person[i]->account_no,person[i]->account_name,&person[i]->phone_no,&person[i]->deposit,&person[i]->dat.day,&person[i]->dat.month,&person[i]->dat.year,person[i]->gender,&person[i]->aadhar,person[i]->debit_issue,person[i]->emailid,person[i]->password);
            }
            else
            {
                printf("WRONG PASSWORD!\n");
            }
           }

        }
        if(!flag)
        {
            printf("ACCOUNT NOT FOUND!\n");
        }
        fclose(old);
        fclose(new1);
        remove("ss.txt");
        rename("new1.txt","ss.txt");
    printf("\nEnter 1 to go to the main menu and 0 to exit:");
            scanf("%d",&main_exit);
            system("cls");
            if (main_exit==1)
                menu();
            else
                close();
}

void menu()
{
    system("cls");
    int choice;
   /* while(1)
   {
       int k = 0;
       static int c = 0;
       if(c)
       {

        printf("Press 1 to return to main menu\n");
        scanf("%d", &k);
   }*/
  // if (k)

    system("COLOR 1B");
    printf("\t\t\t\xB2\xB2\xB2\xB2\xB2\xB2\xB2  WELCOME TO MAIN MENU  \xB2\xB2\xB2\xB2\xB2\xB2\xB2 \n\n\n");
    printf("\t\t\tPress 1 to create new account\n");
    printf("\t\t\tPress 2 to make a transaction\n");
    printf("\t\t\tPress 3 to issue debit card\n");
    printf("\t\t\tPress 4 to link aadhar card\n");
    printf("\t\t\tPress 5 to view account details\n");
    printf("\t\t\tPress 0 to quit\n");
    scanf("%d", &choice);
    //c = 1;
    if(choice==0)
    {
        return;
    }
    switch (choice)
    {
       case 1:
           createAccount();
           break;
       case 2:
            transaction();
            break;
       case 3:
            debit_card();
            break;
       case 4:
            aadhar_set();
            break;
       case 5:
            display_account();
            break;
  //  k = 0;
   // c = 1;

    }
   }

void close()
{
    printf("PROJECT MADE BY 1.SUKANT\n2.SUMIT\n3.SURYASNH\n4.VAIBHAV");
}



int main()
{
   /* person[0] =(struct details*)malloc(sizeof(struct details));
    person[0]->aadhar = NULL;
    strcpy(person[0]->account_name,"sukant");
    person[0]->account_no = 1;
    person[0]->dat.day = 15;
    person[0]->dat.month=12;
    person[0]->dat.year=1111;
    person[0]->deposit = 5000;
    strcpy(person[0]->emailid ,"@GMAIL");
    strcpy(person[0]->gender , "make");
    strcpy(person[0]->password,"okay");
    person[0]->phone_no = 12341414;
    strcpy(person[0]->debit_issue,"NO");
    person[1] =(struct details*)malloc(sizeof(struct details));
    person[1]->aadhar = 999;
    strcpy(person[1]->account_name,"suryansh");
    person[1]->account_no = 2;
    person[1]->dat.day = 15;
    person[1]->dat.month=12;
    person[1]->dat.year=1652;
    strcpy(person[1]->debit_issue,"NO");
    person[1]->deposit = 0;
   strcpy(person[1]->emailid ,"@YAHOO");
    strcpy(person[1]->gender , "male");
  strcpy(person[1]->password,"okaydone");
    person[1]->phone_no = 9797;
*/
 char passw[20];
 char pass[20]="amigos";
 printf("\t\tENTER YOUR PASSWORD\n\t\t");
 fflush(stdin);
 scanf("%s",passw);
 if(strcmp(passw,pass)==0)
 {
    printf("\n\n\t\tPASSWORD MATCHING");
    for(int i=0;i<5;i++)
    {
        fordelay(100000000);
        printf(".");
    }
       fordelay(100000000);
      printf("\n\nLOGIN SUCCESSFUL\n");


     menu();
 }


return 0;
}


