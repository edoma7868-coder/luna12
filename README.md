#include <iostream>
#include <iomanip>
#include <string>
#include <limits>
using namespace std;

int main() {
    string names[5];
    int marks[5][3];
    int total[5];
    float avg[5];

    // Enter student names and marks
    for (int i = 0; i < 5; i++) {
        cout << "\nEnter name of student " << i + 1 << ": ";
        getline(cin, names[i]);

        for (int j = 0; j < 3; j++) {
            cout << "Enter mark " << j + 1
                 << " for " << names[i] << ": ";
            cin >> marks[i][j];
        }

        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }

    // Calculate total and average
    for (int i = 0; i < 5; i++) {
        total[i] = 0;

        for (int j = 0; j < 3; j++) {
            total[i] += marks[i][j];
        }

        avg[i] = total[i] / 3.0;
    }

    // Display the mark sheet
    cout << "\n\n";
    cout << "================ MARK SHEET ================\n";

    cout << left
         << setw(15) << "Name"
         << setw(10) << "Mark 1"
         << setw(10) << "Mark 2"
         << setw(10) << "Mark 3"
         << setw(10) << "Total"
         << setw(10) << "Average" << endl;

    cout << string(65, '-') << endl;

    for (int i = 0; i < 5; i++) {
        cout << left
             << setw(15) << names[i]
             << setw(10) << marks[i][0]
             << setw(10) << marks[i][1]
             << setw(10) << marks[i][2]
             << setw(10) << total[i]
             << fixed << setprecision(2)
             << setw(10) << avg[i] << endl;
    }

    // Find the student with the highest total
    int highest = 0;

    for (int i = 1; i < 5; i++) {
        if (total[i] > total[highest]) {
            highest = i;
        }
    }

    cout << "\n============================================\n";
    cout << "Student with the highest total marks:\n";
    cout << "Name: " << names[highest] << endl;
    cout << "Total: " << total[highest] << endl;
    cout << "Average: " << fixed << setprecision(2)
         << avg[highest] << endl;

    return 0;
}
