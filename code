#include <iostream>
#include <fstream>
#include <iomanip>
#include <vector>
#include <string>
#include <conio.h>
#include <windows.h>
#include <ctime>
using namespace std;

class Item
{
public:
	string name;
	double cost;
	Item(string n, double c) : name(n), cost(c) {}
};

class Receipt
{
private:
	string username;
	vector<Item> items;
	double totalCost;
	string paymentOption;

public:
	Receipt(string user, const vector<Item> &itemList, double cost, string option)
		: username(user), items(itemList), totalCost(cost), paymentOption(option) {}

	void generateReceipt()
	{
		ofstream file("receipt.txt"); // Open the file in write mode
		if (!file)
		{
			cout << "Error creating the file!" << endl;
			Beep(2000, 500);
			return;
		}
		file << "___ RECEIPT ___" << endl
			<< endl;
		file << "Username          : " << username << endl
			<< endl;
		file << "Purchased Items   : " << endl;
		for (const auto &item : items)
		{
			file << "- " << item.name << " : $" << item.cost << endl;
		}
		file << endl;
		file << "Total Cost        : $" << totalCost << endl;
		file << "Payment Option    : " << (paymentOption == "1" ? "Cash on Delivery" : "Credit Card") << endl;
		file << endl
			<< "_________" << endl;
		file.close(); // Close the file
		cout << "Receipt generated and saved to 'receipt.txt'." << endl;
	}
};

class UserAuthentication
{
protected:
	string username;
	string password;

public:
	UserAuthentication()
	{
		username = "";
		password = "";
	}

	void login()
	{
		int i = 0;
		string u, p;
		char pass[7], ch;
		while (1)
		{
			system("cls");
			cout << endl
				<< "\n\n\n\n\n\n\n\n\t\t\t Enter Username : ";
			cin >> u;
			cout << endl
				<< "\t\t\t Enter Password : ";
			for (i = 0; i < 6; ++i)
			{
				ch = _getch();
				pass[i] = ch;
				cout << '*';
			}
			pass[6] = '\0';
			p = "hacker";
			if (u == "Mani" && strcmp(pass, p.c_str()) == 0)
			{
				break;
			}
			else
			{
				system("cls");
				cout << "Username and password entered do not match! Please try again.";
				Beep(2000, 500);
			}
			_getch();
		}
		_getch();
	}

	void welcomeScreen()
	{
		system("color 0b");
		Sleep(700);
		login();
		cout << endl
			<< setw(30) << "Checking Username & Password";
		cout << "                                         " << endl;
		cout << "                                         " << endl;
		cout << " Login Successful." << endl;
		Sleep(700);
		cout << "                                         " << endl;
		cout << " Welcome to Online Shopping System";
		cout << "                                         " << endl;
		cout << endl;
		system("pause");
		system("cls");
	}
};

class OnlineShoppingSystem : public UserAuthentication
{
public:
	void displayCategories()
	{
		system("color 0b");
		cout << "                                         " << endl;
		cout << "      WELCOME TO ONLINE SHOPPING         " << endl;
		cout << "                                         " << endl;
		cout << "      Please choose a category           " << endl;
		cout << "                                         " << endl;
		cout << "Sno." << setw(25) << "Product Category   " << endl;
		cout << "                                         " << endl;
		cout << "1.  " << setw(20) << "Electronics" << endl;
		cout << "                                         " << endl;
		cout << "2.  " << setw(20) << "Clothing   " << endl;
		cout << "                                         " << endl;
		cout << "3.  " << setw(20) << "Books      " << endl;
		cout << "                                         " << endl;
		cout << "4.  " << setw(20) << "Home Decor " << endl;
		cout << "                                         " << endl;
		cout << "5.  " << setw(20) << "Exit       " << endl;
		cout << "                                         " << endl;
	}

	void displayItems(const vector<Item> &items)
	{
		system("color 0b");
		cout << "                Available Items                     " << endl;
		cout << "                                                    " << endl;
		cout << "ID" << setw(20) << "Item   " << setw(25) << "Price" << endl;
		cout << "                                                    " << endl;
		int id = 1;
		for (const auto &item : items)
		{
			cout << id++ << setw(20) << item.name << setw(15) << "\t$" << item.cost << endl;
		}
	}

	void placeOrder(const vector<Item> &items)
	{
		vector<Item> selectedItems;
		char choice;
		displayItems(items);
		cout << endl;
		cout << "Enter item ID(s) to add to cart (separated by space): ";
		size_t id;
		while (cin >> id)
		{
			if (id >= 1 && id <= items.size())
			{
				selectedItems.push_back(items[id - 1]);
			}
			else
			{
				cout << "Invalid item ID. Please try again." << endl;
			}
			if ((choice = cin.get()) == '\n')
			{
				break;
			}
		}
		double totalCost = 0;
		for (const auto &item : selectedItems)
		{
			totalCost += item.cost;
		}
		cout << "Total cost              : $" << totalCost << endl;
		cout << "                                         " << endl;
		cout << "Select payment option   :  " << endl;
		cout << "1. Cash on Delivery" << endl;
		cout << "2. Credit Card" << endl;
		cout << "                                         " << endl;
		string paymentOption;
		cout << " Payment option   :  "; cin >> paymentOption;
		Receipt receipt(username, selectedItems, totalCost, paymentOption);
		receipt.generateReceipt();
	}

	void run()
	{
		displayCategories();
		int choice;
		vector<Item> items;
		do
		{
			cout << "Enter your choice (1-5): ";
			cin >> choice;
			switch (choice)
			{
			case 1:
				items = { Item("Laptop", 999.99), Item("Smartphone", 699.99), Item("Tablet", 299.99) };
				placeOrder(items);
				break;
			case 2:
				items = { Item("T-Shirt", 19.99), Item("Jeans", 39.99), Item("Dress", 49.99) };
				placeOrder(items);
				break;
			case 3:
				items = { Item("Novel", 9.99), Item("Textbook", 59.99), Item("Biography", 29.99) };
				placeOrder(items);
				break;
			case 4:
				items = { Item("Painting", 199.99), Item("Vase", 49.99), Item("Candle Holder", 9.99) };
				placeOrder(items);
				break;
			case 5:
				cout << "                                         " << endl;
				cout << "Thank you for using the Online Shopping System. Goodbye!" << endl;
				break;
			default:
				cout << "Invalid choice. Please try again." << endl;
				Beep(2000, 500);
				break;
			}
			cout << endl;
		} while (choice != 5);
	}
};

int main()
{
	OnlineShoppingSystem oss;
	oss.welcomeScreen();
	oss.run();
	_getch();
	return 0;
}
