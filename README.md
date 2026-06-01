# Registration-and-Login-Form-With-File-Handlin#include <iostream>
#include <fstream>
#include <windows.h>
#include <sstream>
using namespace std;

class Login{
    private:
    string loginID, Password;

    public:
    Login():loginID(""),Password(""){}

    void setID(string id){
        loginID = id;
    }

    void setPw(string pw){
        Password = pw;
    }

    string getID(){
        return loginID;
    }

    string getPw(){
        return Password;
    }
};

void registration(Login log){

    system("cls");

    string id, pw;

    cout<<"\tEnter Login ID: ";
    cin>>id;

    log.setID(id);

    start:

    cout<<"\tEnter A Strong Password: ";
    cin>>pw;

    if(pw.length() >= 8){
        log.setPw(pw);
    }
    else{
        cout<<"\tEnter Minimum 8 Characters!"<<endl;
        goto start;
    }

    ofstream outfile("Login.txt", ios::app);

    if(!outfile){
        cout<<"\tError: File cannot open!"<<endl;
    }
    else{

        outfile<<log.getID()<<":"<<log.getPw()<<endl;

        cout<<"\tUser Registered Successfully!"<<endl;
    }

    outfile.close();

    Sleep(4000);
}

void login(){

    system("cls");

    string id, pw;

    cout<<"\tEnter Login ID: ";
    cin>>id;

    cout<<"\tEnter Password: ";
    cin>>pw;

    ifstream infile("Login.txt");

    if(!infile){

        cout<<"\tError File Can't Open!"<<endl;
    }
    else{

        string line;
        bool found = false;

        while(getline(infile, line)){

            stringstream ss(line);

            string userID, userPw;

            getline(ss, userID, ':');
            getline(ss, userPw);

            if(id == userID && pw == userPw){

                found = true;

                cout<<"\tPlease Wait";

                for(int i=0; i<3; i++){

                    cout<<".";
                    Sleep(800);
                }

                system("cls");

                cout<<"\tWelcome To This Page!"<<endl;

                break;
            }
        }

        if(!found){

            cout<<"\tIncorrect Login ID or Password!"<<endl;
        }

        infile.close();
    }

    Sleep(5000);
}

int main(){

    Login log;

    bool exit = false;

    while(!exit){

        system("cls");

        int val;

        cout<<"\tWELCOME TO REGISTRATION & LOGIN FORM"<<endl;
        cout<<"\t*************************************"<<endl;
        cout<<"\t1. Registration"<<endl;
        cout<<"\t2. Login"<<endl;
        cout<<"\t3. Exit"<<endl;
        cout<<"\tEnter Choice: ";

        cin>>val;

        if(val == 1){

            registration(log);
        }
        else if(val == 2){

            login();
        }
        else if(val == 3){

            exit = true;

            cout<<"\tGood Luck!"<<endl;

            Sleep(2000);
        }
        else{

            cout<<"\tInvalid Choice!"<<endl;

            Sleep(2000);
        }
    }

    return 0;
}g-OOP-c-
It help me to buit my understanding in coding espacially OOP In C+++
