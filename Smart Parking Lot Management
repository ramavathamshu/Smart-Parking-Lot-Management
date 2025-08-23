#include <iostream>
#include <string>
using namespace std;

// Node structure for linked list
struct Car {
    string regNumber;
    Car* next;
};

// ParkingLot class
class ParkingLot {
private:
    Car* head;      // head pointer to linked list
    int capacity;   // total slots
    int count;      // currently occupied

public:
    // Constructor
    ParkingLot(int size) {
        capacity = size;
        count = 0;
        head = nullptr;
    }

    // Destructor to free memory
    ~ParkingLot() {
        while (head != nullptr) {
            Car* temp = head;
            head = head->next;
            delete temp;
        }
    }

    // Add a car (Entry)
    void parkCar(string reg) {
        if (count >= capacity) {
            cout << "Parking Lot Full! Cannot park car " << reg << endl;
            return;
        }

        Car* newCar = new Car{reg, nullptr};

        if (head == nullptr) {
            head = newCar;
        } else {
            Car* temp = head;
            while (temp->next != nullptr)
                temp = temp->next;
            temp->next = newCar;
        }

        count++;
        cout << "Car " << reg << " parked successfully." << endl;
    }

    // Remove a car (Exit)
    void removeCar(string reg) {
        if (head == nullptr) {
            cout << "Parking Lot Empty!" << endl;
            return;
        }

        Car* temp = head;
        Car* prev = nullptr;

        while (temp != nullptr && temp->regNumber != reg) {
            prev = temp;
            temp = temp->next;
        }

        if (temp == nullptr) {
            cout << "Car " << reg << " not found!" << endl;
            return;
        }

        if (prev == nullptr) {
            head = head->next; // car is at head
        } else {
            prev->next = temp->next;
        }

        delete temp;
        count--;
        cout << "Car " << reg << " removed successfully." << endl;
    }

    // Display parked cars
    void display() {
        if (head == nullptr) {
            cout << "No cars parked currently." << endl;
            return;
        }

        cout << "Currently Parked Cars (" << count << "/" << capacity << "):" << endl;
        Car* temp = head;
        while (temp != nullptr) {
            cout << "- " << temp->regNumber << endl;
            temp = temp->next;
        }
    }
};

// Main Program
int main() {
    int n;
    cout << "Enter Parking Lot Capacity: ";
    cin >> n;

    ParkingLot lot(n);

    int choice;
    string reg;

    do {
        cout << "\n--- Smart Parking Lot Menu ---\n";
        cout << "1. Park Car\n2. Remove Car\n3. Display Parked Cars\n4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter Car Registration Number: ";
                cin >> reg;
                lot.parkCar(reg);
                break;
            case 2:
                cout << "Enter Car Registration Number to Remove: ";
                cin >> reg;
                lot.removeCar(reg);
                break;
            case 3:
                lot.display();
                break;
            case 4:
                cout << "Exiting..." << endl;
                break;
            default:
                cout << "Invalid choice!" << endl;
        }
    } while (choice != 4);

    return 0;
}
