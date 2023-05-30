# CSE_project
Bank Login Portal


The Bank Login Portal project is a web application that provides a secure and user-friendly interface for customers to log in to their bank accounts. It is designed to enhance security and streamline the login process, ensuring a seamless banking experience for users.


The code I provided is a C++ program for a Bank Login Portal. It allows users to create a new account, access existing accounts, check balance, update passwords, transfer money, and perform other related actions.

The code defines a class called "info" to store information about bank account holders. It includes member variables such as first name, last name, Aadhaar number, address details, phone number, password, Gmail address, and account balance.

The program uses various functions to validate user input, such as Aadhaar number, phone number, and Gmail address. It ensures that the input meets certain criteria before proceeding with the account creation or login process.

To test the code, you can run it and interact with the program using the provided sample data. The program will simulate the bank login portal, allowing you to create a new account or access an existing account based on the options you choose.

To test out my project, what you need to know:-
1- Preloaded sample data for testing
sample - 1
    First name -"Udit"
    Last name-"Sharma"
    State-"Rajasthan"
    District-"Sawai Madhopur"
    City-"Sawai Madhopur"
    Password-"12345"
    Gmail-"example@gmail.com"
    Aadhar no-"123456781234"
    Phone no-"0000000000"
    Account Balance-10000
sample - 2
    First name -"Viraj"
    Last name-"Pradhan"
    State-"Maharashtra"
    District-""Mumbai"
    City-"Dombivili"
    Password-"54321"
    Gmail-"viraj@gmail.com"
    Aadhar no-"000000000000"
    Phone no-"1234567890"
    Account Balance-20000
    
2- Default OTP : 0000
   Default Gmail Verification code : 1234
   Default Payment Verification code : 1111



This is the code for my project

#include <iostream>
#include <string>
#include <cstdio>
using namespace std;

bool validate_aadhar(const std::string& aadhar_number) {
    if (aadhar_number.length() != 12) {
        return false;
    }

    for (char c : aadhar_number) {
        if (c < '0' || c > '9') {
            return false;
        }
    }

    return true;
}

bool validate_phone(const std::string& phone_number) {
    if (phone_number.length() != 10) {
        return false;
    }

    for (char c : phone_number) {
        if (c < '0' || c > '9') {
            return false;
        }
    }

    return true;
}

bool validate_gmail(const std::string& gmail_address) {
    if (gmail_address.length() < 5 || gmail_address.length() > 320) {
        return false;
    }

    size_t at_pos = gmail_address.find('@');
    if (at_pos == std::string::npos || at_pos == 0 || at_pos == gmail_address.length() - 1) {
        return false;
    }

    return true;
}

bool is_numbers_only(const std::string& str) {
    for (char c : str) {
        if (c < '0' || c > '9') {
            return false;
        }
    }
    return true;
}


class info{
  public:
  string firstName,lastName,
  aadharNo,
  adress_state,adress_district,adress_city,
  phoneNo,password,
  Gmail;
  int balance;

  void getData(string fn,string ln,string as,string ad,string ac,string p,string gm,string aNo,string pNo,int b)
  {
    firstName =fn; lastName =ln;
    adress_state =as; adress_district =ad; adress_city = ac;
    password=p;
    aadharNo=aNo,phoneNo=pNo,balance=b;
    Gmail = gm;
  }

  void getBalance()
  {
    cout<<balance;
  }
};

int main()
{ 
  /*
  For testing the code , here we have a database of accountholders you can use it to test the code.
  */

  info i[100];
  i[0].getData("Udit","Sharma","Rajasthan","Sawai Madhopur","Sawai Madhopur","12345","example@gmail.com","123456781234","0000000000",100000);
  i[1].getData("Viraj","Pradhan","Maharashtra","Mumbai","Dombivli","54321","viraj@gmail.com","000000000000","1234567890",200000);


  string tempName1,tempName2;
  int j=1;
  while(3>2){
    cout<<"Hello,This is your personal assistant"<<endl<<"Enter your first name: ";
    getline(cin >> tempName1, tempName2);
    while(1>0){
      int x=3;
      x++;
      string commandNo;
      cout<<endl<<"What would you like to do , "<<tempName1<<"?"<<endl
        <<"1 - Create a new account"<<endl
        <<"2 - Access an existing account"<<endl
        <<"3 - Exit"<<endl;
      cout<<endl<<"Enter the number associated with your command"<<endl;
      cin>>commandNo;
      if(commandNo=="3"){break;}

      else if(commandNo=="1")
      {
        j++;
        string first_name1,first_name2,
               last_name1,last_name2,
               taadharNo,
               State1,State2,
               District1,District2,
               City1,City2,
               phoneNo,otp,
               temail1,temail2,ecode;
        
        cout<<endl<<"Enter your first name: ";
        getline(cin >> first_name1,first_name2);
        
        cout<<endl<<"Enter your second name: ";
        getline(cin >> last_name1,last_name2);
        

        while(true){
        cout<<endl<<"Enter your Aadhaar number: ";
        cin >> taadharNo;
        if (validate_aadhar(taadharNo))
        {
          break;
        } 
        else
        {
          cout <<"Invalid Aadhaar number , please retry" <<endl;
        }
        }
        
        
        cout<<endl<<"Enter you State:";
        getline(cin >> State1, State2);

        cout<<endl<<"Enter you District:";
        getline(cin >> District1, District2);
        
        cout<<endl<<"Enter you City:";
        getline(cin >> City1, City2);
        

        while(true)
        {
        cout <<endl<<"Enter your phone number: ";
        cin >> phoneNo;

        if (validate_phone(phoneNo))
        {
          break;
        }
        else
        {
          cout << "Invalid phone number , please retry" << endl;
        }
        }

        while(true){
        cout<<endl<<"Enter Verification OTP"<<endl;
        cin>>otp;
        if(otp=="0000")
        {
          cout<<endl<<"Phone no verified successfully!"<<endl;
          break;
        }
        else
        {
          cout<<"Invalid OTP"<<endl;
        }
        }


        while(true){
        cout <<endl<< "Enter your Gmail address: ";
        getline(cin >> temail1, temail2);

        if (validate_gmail(temail1))
        {
          break;
        }
        else
        {
          cout << "Invalid Gmail address , please retry" << endl;
        }
        }
        
        while(true){
        cout<<endl<<"Enter Verification Code: ";
        cin>>ecode;
        if(ecode=="1234")
        {
          cout<<endl<<"Gmail Verified successfully!"<<endl;
          break;
        }
        else
        {
          cout<<"Invalid Code"<<endl;
        }
        }


        cout<<"To activate your account."<<endl
            <<"You must deposite a minimum amount of 1000 rupees."<<endl;
        cout<<endl<<"Now you will be redirected to payment portal"<<endl;
        cout<<endl<<"-----------------------------------------------------------------------"<<endl<<endl;

        string upiId,tupiId,pCode;
        int amount;
        cout<<"Enter your UPI id: ";
        getline(cin >> upiId ,tupiId);
        while(true){
        cout<<endl<<"Enter the amount: ";
        cin>>amount;
        if(amount<1000)
        {
          cout<<"You must deposite a minimum of 1000 rupees to activate your account."<<endl;
        }
        else{break;}
        }

        cout<<"A payment request has been sent to you UPI id"<<endl
            <<"waiting for payment to be done."<<endl<<endl
            <<"A 4-digit payment verification code has been set on your registered mobile no."<<endl<<endl;

        while(true){
        cout<<endl<<"Enter the code: "<<endl;
        cin>>pCode;
        if(pCode=="1111")
        {
          cout<<endl<<"Transaction Completed"<<endl;
          break;
        }
        else
        {
          cout<<"Invalid code"<<endl;
        }
        }
        cout<<"Succesfully created you account"<<endl;

        int tbalance=0;
        tbalance+=amount;

        cout<<endl<<"You need to set a password to access you account"<<endl;

        string password1,tpassword1,
               password2,tpassword2;
        while(true){
        cout<<endl<<"Enter the password: ";
        getline(cin >> password1 ,tpassword1);
        cout<<endl<<"Confirm password: ";
        getline(cin >> password2 ,tpassword2);

        if(password1==password2)
        {
          cout<<endl<<"Password created succesfully!"<<endl;
          break;
        }
        else
        {
          cout<<"Passwords do not match , please retry"<<endl;
        }
        }

        cout<<endl<<"Congratulations!!"<<endl
            <<"You have completed all the steps to create a account"<<endl
            <<endl<<"Now you can access you account with your username and password"<<endl
            <<"Note - Your username will be your first name(only)"<<endl;
        cout<<endl<<"---------------------------------------------------------------------------------"<<endl;

        cout<<endl<<"Redirecting to the menu page";

        // Inserting all the input data in our database (class)
        i[j].getData(first_name1,last_name1,State1,District1,City1,password1,temail1,taadharNo,phoneNo,tbalance); 
      }


      else if(commandNo=="2")
      {
        string tUsername_1,tPassword_1,
               tUsername_2,tPassword_2;
        int x=90,count;
        input:
        cout<<"Enter Username [first name]: ";
        getline(cin>>tUsername_1,tUsername_2);
        for(int j=0;j<100;j++)
        {
          if(tUsername_1==i[j].firstName)
          {
            x=j;
          }
        }

        if(x==90)
        {
          cout<<"No such username found , please retry"<<endl<<endl;
          goto input;
        }
        
        while(true)
        {
        cout<<endl<<"Enter Password: ";
        getline(cin>>tPassword_1,tPassword_2);
        if(tPassword_1==i[x].password)
        {
          cout<<"Logged in successfully!"<<endl;
          break;
        }
        else
        {
          cout<<"Incorrect Password , please retry"<<endl;
        }
        }
        while(true){
        cout<<endl<<"What would you like to do , "<<tUsername_1<<"?"<<endl
        <<"0 - Profile"<<endl
        <<"1 - Check Balance"<<endl
        <<"2 - Update Password"<<endl
        <<"3 - Transfer money"<<endl
        <<"4 - Logout"<<endl;

        string temp_comm;
        cin>>temp_comm;
        if(temp_comm=="4"){break;}

        else if(temp_comm=="0")
        {
          cout<< "First name - "<<i[x].firstName<<endl
              << "Last name - "<<i[x].lastName<<endl
              << "State - "<<i[x].adress_state<<endl
              << "District - "<<i[x].adress_district<<endl
              << "City - "<<i[x].adress_city<<endl
              << "Gmail - "<<i[x].Gmail<<endl
              <<"Aadhar no - "<<i[x].aadharNo<<endl
              <<"Phone no - "<<i[x].phoneNo<<endl;
        }

        else if(temp_comm=="1")
        {
          cout<<endl<<"Your current account balance is: "<<i[x].balance<<" rupees"<<endl;
        }

        else if(temp_comm=="2")
        {
          string old_pass_1,old_pass_2,
                 new_pass_1,con_new_pass_1,
                 new_pass_2,con_new_pass_2;
          while(true){
          cout<<"Enter current password: ";
            getline(cin>>old_pass_1,old_pass_2);
            if(old_pass_1==i[x].password)
            {
              break;
            }
            else
            {
              cout<<"Incorrect Password , please retry"<<endl<<endl;
            }
          }
          
          while(true){
          cout<<endl<<"Enter new password: ";
          getline(cin>>new_pass_1,new_pass_2);
          cout<<endl<<"Confirm password: ";
          getline(cin>>con_new_pass_1,con_new_pass_2);

          if(new_pass_1==con_new_pass_1)
          {
            cout<<endl<<"Password updated succesfully!"<<endl;
            i[x].password=new_pass_1;
            break;
          }
          else
          {
            cout<<"Passwords do not match , please retry"<<endl;
          }
          }
        }

        else if(temp_comm=="3")
        {
          string rec_account_1,rec_password_1,
                 rec_account_2,rec_password_2;
          int rec_amount;

          while(true){
          cout<<endl<<"Enter the reciever's account number: ";
          getline(cin>>rec_account_1,rec_account_2);
          if (is_numbers_only(rec_account_1))
          {
            break;
          }
          else
          {
            cout<<"Invalid Account number , please retry"<<endl;
          }
          }

          while(true){
          cout<<endl<<"Enter the amount: ";
          cin>>rec_amount;
          if(rec_amount>(i[x].balance-1000))
          {
            cout<<"Amount exceeding minumum limit , please retry"<<endl;
          }
          else{break;}
          }

          
          while(true)
          {
            cout<<endl<<"Enter Password: ";
            getline(cin>>rec_password_1,rec_password_2);
            if(rec_password_1==i[x].password)
            {
              cout<<endl<<"Transaction Completed"<<endl;
              i[x].balance-=rec_amount;
              break;
            }
            else
            {
              cout<<"Incorrect Password , please retry"<<endl;
            }
          }
        }
        }
      }
    }
  }
}
