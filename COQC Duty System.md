#include <iostream>
#include <string>
#include <iomanip>
#define BOLD    "\033[1m"  //BOLD TEXT
#define RED     "\033[31m" //RED
#define GREEN   "\033[32m" //GREEN
#define RESET   "\033[0m"  //RESET COLOR

using namespace std;

const int week = 6;         //day in a week to duty
const int minimumHour = 3;  //minimum of 3 hours duty within the week

int ans = 1; //looping to access the inner code
int yes = 2; //looping to duty again

void inputCredentials(string& name, string& id, string& course); //credential of COQC
int inputDutyHours(int dutyHour[]);                             //for input of duty
int calculateTotalHours(int dutyHours[]);                        //calculation for duty hour

void design();
void header();

    void inputCredentials(string& name, string& id, string& course) //input of credentials
    {
        cout << "*****************************************************************\n";
        cout << "*                        LOGIN SYSTEM                           *\n";
        cout << "*****************************************************************\n";
        cout << "        Enter Full Name: ";
        cin.ignore();
        getline(cin, name);
        cout << "        Enter School ID: ";
        cin >> id;
        cout << "        Enter Course   : ";
        cin >> course;
        cout << "*****************************************************************\n";

        system("pause");
        system("cls");

        cout << BOLD;
        cout << "***********************************************\n";
        cout << "*               COQC CREDENTIALS              *" << endl;
        cout << "***********************************************" << endl;
        cout << "    COQC NAME : " << name << endl;                         //
        cout << "    STUDENT NO: " << id   << endl;                         //output of the credentials
        cout << "    COURSE    : " << course << endl;                       //
        cout << "***********************************************" << endl;
        cout << "* REMINDER:IF YOU NOT DUTY ON THAT DAY TYPE 0 *" << endl;
        cout << "***********************************************\n" << endl;
        cout << RESET << endl;
    }

    int inputDutyHours(int dutyHour[])
    {
        for (int d = 1; d <= week; ++d)
        {
            cout << "Enter duty hours for day " << d << ": ";
            cin >> dutyHour[d];
        }
    }

    int calculateTotalHours(int dutyHours[])
    {
        int totalHours = 0;
        for (int i = 1; i <= week; ++i)
        {
            totalHours += dutyHours[i];
        }
        return totalHours;
    }



int main() {
    string name;
    string id;
    string course;
    int dutyHours[week];

    header();
    cout << BOLD;
    cout << "* ACCESS THE DUTY SYSTEM (PRESS 1 TO PROCEED, 0 TO EXIT): ";
    cin >> ans;
    cout << "*****************************************************************\n";
    cout << RESET << endl;

    while (ans == 1)
    {
        // Input credentials
        inputCredentials(name, id, course);
        // Input duty hours
        inputDutyHours(dutyHours);
        // Calculate total hours
        int totalHours = calculateTotalHours(dutyHours);

        cout << endl;
        cout << endl;
        design();
        cout << BOLD << "     WEEKLY DUTY REPORT:   " << name << " (" << course << ")"<< endl; // Display report
        cout << endl;
        cout << "     TOTAL DUTY HOURS: " << totalHours << "hrs" << RESET << endl;


        if (totalHours >= minimumHour) {
            cout << GREEN << "*    You have met the minimum weekly duty hour requirement.\n" << RESET;
        } else {
            cout << RED <<"*    You have not met the minimum weekly duty hour requirement.\n";
            cout << "*                  See you on training day. (:\n" << RESET;
        }
        design();

        cout << "Do you want to duty again? (PRESS 1 FOR YES, 0 FOR NO): ";
        cin >> ans;
        system("cls");
    }

    return 0;


}

                    //design and header part
void design() {
    cout << "*********************************************************************" << endl;
}

void header() {
    cout << BOLD;
    cout << "*****************************************************************\n";
    cout << "*                      COQC DUTY SYSTEM                         *\n";
    cout << "*****************************************************************\n";
    cout << "*  Description: The COQC Duty System is designed to streamline  *\n";
    cout << "*               the scheduling and management of weekly duties  *\n";
    cout << "*               for COQC. This system allows COQC to input      *\n";
    cout << "*               their duty hours for each day of a week.        *\n";
    cout << "*                                                               *\n";
    cout << "*  Creator: EDWOOD MENDOZA                                      *\n";
    cout << "*  Course : DIT-1                                               *\n";
    cout << "*                                                               *\n";
    cout << "*  Publish date: February 10, 2024                              *\n";
    cout << "*                                                               *\n";
    cout << "*****************************************************************" << RESET << endl;
}
