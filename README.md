# Adi-Chavan-08
// My First Project Is "Class Fees Management System"

#include<iostream>
#include<fstream>
using namespace std;

class Log{
    private:
        string name,email, pass;
        string temp,tempemail,temppass;
        fstream file;
        
    public:
        void signup();
        int login();
        void forget();
        void logout();
}obj;
class Fees: public Log
{
    string sname,t,fee;
    fstream file1;
    public:
        void enterData();
        void details();
        void showall();
}obj1;
int main()
{
    int o,ch;
    
    cout<<"1:Sign Up\t2: Login\t3: Forget Password\n4:Exit"<<endl;
    cout << "Enter A choice" << endl;
    cin>>ch;
    switch(ch){
        case 1:
        cin.ignore();
            obj.signup();
            break; 
        case 2:
        cin.ignore();
          o=obj.login();
            break;
        case 3:
        cin.ignore();
            obj.forget();
            break;
        case 4:
           exit(1);
        default:
            cout << "invalid choice" << endl;
            
    }
    if(o==1)  
    {
    cout << "" << endl;
    cout<<"_______________________________"<<endl<<endl;
    cout << "|WELCOME TO RAHUL_SIR_ACCADAMY|" << endl;
    cout<<endl<<"____________________________________"<<endl;
        while(1){
        cout << "1:Add Students\t2:Show Details\t3:All Students Details\t4:exit" << endl;
        cout << "Enter a choice" << endl;
        cin >> ch;
        switch(ch)
        {
            case 1:
                cin.ignore();
                obj1.enterData();
                break;
            case 2:
                cin.ignore();
                obj1.details();
                break;
                case 3:
                    cin.ignore();
                    obj1.showall();
                    break;
            case 4:
                obj1.logout();
            default:
                cout << "invalid choice" << endl;
                
        }
        
        }
        
    }
    else if(o==0)
    {
        
        cout <<endl<< "USER ID IS INVALID \nRetry..!" << endl;
    }
    cout<<endl<<endl;
    cout<<"       **********       "<<endl;
    cout << "THANKS FOR VISITING..!" << endl;
    cout<<"       **********       "<<endl;
    return 0;
}

void Log:: signup()
{
    cout<<"____________________________________"<<endl;
    cout << "-------SING UP--------" << endl;
    cout<<"____________________________________"<<endl;
    cout << "Enter A User Name" << endl;
    getline(cin,name);
    cout << "Enter A Email" << endl;
    getline(cin,email);
    cout << "Enter A Password" << endl;
    getline(cin,pass);
    
    file.open("loginid.txt",ios::out||ios::app);
   file<<name<<"*"<<email<<"*"<<pass<<endl;
    file.close();
    cout<<"____________________________________"<<endl;
    cout << "SING UP SUCCESSFULLY......! " << endl;
    cout<<"____________________________________"<<endl;
}
int Log::login()
{
    cout<<"____________________________________"<<endl;
    cout << "-------Login--------" << endl;
    cout<<"____________________________________"<<endl;
    cout << "Enter A User Name Or Email" << endl;
    getline(cin,temp);
    cout << "Enter A Password" << endl;
    getline(cin,temppass);
    
    file.open("loginid.txt",ios::in);
    getline(file,name,'*');
    getline(file,email,'*');
    getline(file,pass,'\n');
   while(!file.eof()){

        if(name == temp||email==temp){

            if(pass == temppass){
            cout<<"____________________________________"<<endl;

                cout<<"\nAccount Login Succesfull...!";

                cout<<"\nUsername :: "<<name<<endl;

                cout<<"Email :: "<<email<<endl;
                cout<<"____________________________________"<<endl;
                return 1;

            }else{

                cout<<"Password is Incorrect...!";

            }
            

        }
        else{
        return 0;
        }
        

    getline(file,name,'*');

    getline(file,email,'*');

    getline(file,pass,'\n');

    }
    file.close();

}

void Log::forget()
{
    cout<<"____________________________________"<<endl;
    cout << "-------FORGET PASSWORD--------" << endl;
    cout<<"____________________________________"<<endl;
    cout << "Enter A User Name" << endl;
    getline(cin,temp);
    cout << "Enter A Email" << endl;
    getline(cin,tempemail);
    
    file.open("loginid.txt",ios::in);
    getline(file,name,'*');
    getline(file,email,'*');
    getline(file,pass,'\n');
    while(!file.eof())
    {
        if(name==temp)
        {
            if(email==tempemail)
            {
                cout<<"____________________________________"<<endl;
                cout << "Username:-" << name<<endl;
                cout << "Account Email:-" <<email<< endl;
                cout << "Password;-"<<pass << endl;
                cout<<"____________________________________"<<endl;
            }
            else{
                cout << "Invalid Password" << endl;
            }
        }
        getline(file,name,'*');
        getline(file,email,'*');
        getline(file,pass,'\n');
        }
    file.close();
}

void Fees::enterData()
{
    cout << "Enter Student Name" << endl;
    getline(cin,sname);
    cout << "Enter Remaining Fee " << endl;
    getline(cin,fee);
    
    file1.open("student.txt",ios::out || ios::app);
    file1<<sname<<"*"<<fee<<endl;
    file1.close();
    cout<<"____________________________________"<<endl;
    cout << "Enter Successfully" << endl;
    cout<<"____________________________________"<<endl;
    
}

void Fees::details()
{
    cout << "Enter A search Student Name Or Fees" << endl;
    getline(cin,t);
    
    file1.open("student.txt",ios::in);
    getline(file1,sname,'*');
    getline(file1,fee,'\n');
    while(!file1.eof())
    {
        if(sname==t||fee==t)
        {
            cout<<"____________________________________"<<endl;
            cout << "Detail is::" << endl;
            cout<<sname<<"\t"<<fee<<endl;
            cout<<"____________________________________"<<endl;
        }
        getline(file1,sname,'*');
    getline(file1,fee,'\n');
    }
    file1.close();
}
void Fees::showall()
{
    file1.open("student.txt",ios::in);
    getline(file1,sname,'*');
    getline(file1,fee,'\n');
    cout << "STUDENTS DETAILS" << endl;
    while(!file1.eof())
    {
            cout<<"____________________________________"<<endl;
            cout<<sname<<"\t"<<fee<<endl;
            cout<<"____________________________________"<<endl;
        
        
        getline(file1,sname,'*');
    getline(file1,fee,'\n');
    }
    file1.close();
}
void Log:: logout()
{
    cout<<endl<<endl;
    cout<<"_____________*********_____________"<<endl;
    cout << "THANKS FOR VISITING..!" << endl;
    cout<<"______________*********____________"<<endl;
    cout << "LOG OUT:- " ;
   return  exit(1);
}
