//# Bank-ATM._system.cpp
//I am a Fresh Software Eng student and this is an my First Project on Bank/ATM system
#include<iostream>
using namespace std;
  struct account 
{
    int cardNumber;
    int pin;
    float Balance;
};
void addcard( account acc[], int &count )
{
     cout << "\n--- Add New Card ---\n";
     cout<<"~~Enter New Card Details~\n\n";
     cout<<"Enter Card number: ";
     cin>>acc[count].cardNumber;
     cout<<"Set Pin-code: ";
     cin>>acc[count].pin;
     cout<<"\nEnter initial Deposit: ";
     cin>>acc[count].Balance;
     cout <<"$-Account Created Successfully-$\n";
     count++;
}
int findaccount(account acc[], int count, int cardNO)
{
    for (int i = 0; i < count; i++)
    {
        if (acc[i].cardNumber == cardNO)
        {
            return i;
        }
    }
    return -1;
}

    void atmMenu(account &my){
      int n;
      float amount;
     do { 

      cout<<"\n$----ATM MENU----$\n";
      cout<<"///-Welcome-///\n\n";
      cout<<"1. Check Balance\n";
      cout<<"2. Deposit\n";
      cout<<"3. Withdraw\n";
      cout<<"4. Logout\n";
      cin>>n;
      switch (n)
      {
      case 1:
        cout<<" Your Current Balance: "<<my.Balance<<endl;
        break;
      case 2:
        cout<<"Enter Deposit amount: ";
        cin>>amount;
        if (amount>0)
        {
          my.Balance=my.Balance+amount;
          cout<<amount<<" Deposited Succefully!!!\n";
        }
        else
        {
          cout<<" Invalid Amount\n";
        }
        cout<<"\nUpdated Balance= "<<my.Balance;
        break;
        case 3:
        cout<<"Enter amount to withdraw: ";
        cin>>amount;
         if (amount>0 && amount<=my.Balance)
         {
           my.Balance-=amount;
           cout<<"---withdraw Succesfully---\n";
           cout<<" Remaining Balance = "<<my.Balance<<endl;
         }
        else
        cout<<"< Insufficient Balance >\n";
        break;
        case 4:
        cout << "Exiting.....\n";
        break;
      default:
      cout<<"Invalid Choice"<<endl;
      } 
       
  }  
   while (n!=4);
} 

int main()
 { 
  system ("cls");
    account acc[10];
    int count=0;
    int choice;
    cout<<"Enter Card and press 'Enter' key "<<endl;
    cin.get();
    do {
    cout<<"\n----ATM System----\n";
    cout<<"1. Add Card\n";
    cout<<"2. Login\n";
    cout<<"3. Exit\n";

    cout<<"Enter your choice: ";
    cin>>choice;
    switch (choice)
    {
    case 1:
      addcard(acc, count);
      break;
    case 2:
    {
      
      int cardno;
      int pin;
      cout<<"|--``Welcome``--|"<<endl;
      cout<<"\nEnter your card number: ";
      cin>>cardno;

      int index= findaccount(acc, count, cardno);
      if (index==-1)
      {
        cout<<"\nCard not found!!"<<endl;
      }
      else
      {
        cout<<"Enter password: ";
        cin>>pin;

        if (acc[index].pin==pin)
        {
         atmMenu(acc[index]);
        }
        else
        cout<<"OOPs Wrong Pin!\n";

      }
    }
    break;
    case 3:
    cout<<"``Thank You for Using ATM``"<<endl;
    break;

    default: 
    cout<<"Enter valid Choice..?";
      return 0;
    }
    } 
    while (choice!=3);
     cout << "\n=================================================\n";
    cout << "                PROGRAM ENDED";
    cout << "\n=================================================\n";
return 0;
}
