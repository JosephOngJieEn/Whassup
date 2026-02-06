#include <iostream>
#include <string>
#include <iomanip>
#include <limits> 
using namespace std;

struct Flower{
    string flower_code;
    string flower_name;
	float flower_price;
	float flower_default_sales;
	
    Flower *next;
};

struct flowerCart{ //Linked List for flower cart
	string cartFcode;
	string cartFname;
	float cartFprice;
	int cartFqty;
	flowerCart *next;
};

void menu(Flower *temp,Flower *head) // To display all the flowers
{
	cout << "\n=============================== Flowers Menu ==============================" << endl;
    cout << left << setw(10) << "Code" << setw(35) << "Flowers \t \t \t \t \t \t Price (RM)" << endl;
    cout << "---------------------------------------------------------------------------" << endl;

    temp = head;
    while (temp != NULL) {
        cout << setw(10) << temp->flower_code << setw(35) << temp->flower_name << fixed << setprecision(2) << setw(18) <<"\t"<< temp->flower_price << endl;
        temp = temp->next;
    }

    cout << "----------------------------------------------------------------------------" << endl;
}

class InventoryManagement{
	private:
    int choice;
    char continuee;
    Flower *head, *temp, *prev, *ins;

	public:
    InventoryManagement()
	{ // To declare the existing flowers and make it easier to put it into the linked list
			
			string flowerCode[] = {"BB01", "LL01", "PY01", "RS01", "LY02", "OC01", "CN01", "RS02", "OC02", "CN02", "PY02"};
			string flowerNames[] = {"Baby's Breath", "Asiatic Lily", "Coral Sunset", "Hybrid Tea Rose", "Oriental Hybrid", "Moth Orchid", "Giant Carnation", "Wild Rose", "Cattleya Orchid", "Can-Can Series", "Bernhardt Peony"};
			float flowerPrices[] = {5.00, 8.50, 12.00, 10.00, 9.00, 15.00, 6.00, 9.00, 16.00, 8.00, 11.00};
			int flowerDefaultSales[] = {58, 65, 88, 98, 100, 255, 150, 55, 48, 70, 177};
			int i;
			head = new Flower;
			
			head->flower_code = flowerCode[0];
			head->flower_name = flowerNames[0];
			head->flower_price = flowerPrices[0];
			head->flower_default_sales = flowerDefaultSales[0];
			head->next = NULL;
			temp = head;
			
			for(i=1; i<=10; i++)
			{
				
				temp->next = new Flower;
				temp =  temp->next;
				temp->flower_code = flowerCode[i];
				temp->flower_name = flowerNames[i];
				temp->flower_price = flowerPrices[i];
				temp->flower_default_sales = flowerDefaultSales[i];
				temp->next = NULL;
			}
			
	}

        void verify()
        {   
            string *id = new string;
            string password;
            cout<< "Please enter your manager ID      : ";
            cin>> *id;
            do
            {
                cout << "Please enter the manager password : "; 
                cin >> password;

                if (password == "p22word2") //wrong password cant have access
                {
                    do
                    {
                        display_admin_menu();
                        cout << "Enter your choice : ";
                        cin >> choice;

                        while(choice > 5)
                        {
                            cout << "Invalid selection. Please reselect : ";
                            cin>>choice;
                        }

                        switch(choice)
                        {
                            case 1:
                                add_flower(); 
                                break;

                            case 2:
                                delete_flower();            
                                break;
                                
                            case 3:
                                manage_flower();             
                                break;
                                
                            case 4:
                                generate_sales();
                                break;

                            case 5:
                                cout << "Exiting Manager Menu..." << endl;
                                return;

                            default: break;
                        }
                    
                    } while (continuee == 'Y' || continuee == 'y'); 
                    
                }
                else
                {
                    cout << "Invalid Login Attempt. Please try again." << endl << endl;
                }
            } while (password != "p22word2");
            
            delete id; 
        }

        void display_admin_menu() 
        {
            cout << "\n==================== Admin Menu ====================" << endl;
            cout << "1. Add a new flower" << endl;
            cout << "2. Delete a flower" << endl;
            cout << "3. Manage flower details" << endl;
            cout << "4. Generate sales report" << endl;
            cout << "5. Exit" << endl;
            cout << "======================================================" << endl;
        }
        
        void add_flower()
        {   
            cout<<"\nCurrent Available Flower \n"<<endl;
            menu(temp,head);

            string newcode;
            cout<<"Enter the a new flower code : ";
            cin>>newcode;

            // Check if the new flower code already exists
            temp = head;
            while (temp != NULL) 
            {   
                if (temp->flower_code == newcode) 
                {
                    cout << "Flower with code " << newcode << " already exists. Please try again." << endl;
                    cout<<"\nIf you want to continue to use program press[Y/y] : ";
                    cin>>continuee;
                    return;
                }
                temp = temp->next;
            }

            ins = new Flower;
            ins->flower_code = newcode;
            cout<<"Enter the new flower name : ";
            cin.ignore();
            getline(cin, ins->flower_name);
            cout<<"Enter the new flower price : ";
            cin>>ins->flower_price;
            ins->next = NULL;

            if (head == NULL) 
            {
                head = ins; // If the list is empty, ins becomes the head
            } 

            else 
            {
                temp = head;
                while (temp->next != NULL) 
                {
                    temp = temp->next;
                }
                temp->next = ins; // Append newFlower at the end of the list
            }

            cout << "New flower added successfully." << endl;

            cout<<"\nYou are done, Manager ! If you want to continue to use program press [y / Y] : ";
            cin>>continuee;
            cout<<"\n"<<endl;
        }
        
        void delete_flower()
        {
            menu(temp, head);

            string target;
            cout<<"Enter the flower code : ";
            cin>>target;

            temp = head;

            //searching using linear search
            while ((temp != NULL) && (temp->flower_code != target))
            {
                prev = temp;
                temp = temp->next;
            }

            if(temp != NULL && temp->flower_code == target)
            {
                if(head->flower_code == target)
                {

                    head=head->next;
                    delete temp;
                }
                
                else 
                {
                    prev->next = temp->next;
                    delete temp; 
                }
                cout << "Flower deleted successfully." << endl;
                cout<<"\nYou are done, Manager ! If you want to continue to use program press [y / Y] : ";
                cin>>continuee;
                cout<<"\n"<<endl;
                
            }
            
            else
            {
                cout << "Invalid flower code. Please try again." << endl;
                cout<<"\nIf you want to continue to use program press [y / Y] : ";
                cin>>continuee;
                cout<<"\n"<<endl;
            }
            
            
        }
        
        void manage_flower()
        {
            menu(temp, head);

            string target;
            
            cout<<"Enter the flower code : ";
            cin>>target;

            temp = head;

            //searching using linear search
            while (temp != NULL && temp->flower_code != target)
            {
                temp = temp->next;
            }

            if(temp!=NULL && temp->flower_code == target)
            {
                cout<<"~~~~~~~~~~~~~~~You Have Selected "<<temp->flower_code<<"\t"<<temp->flower_name<<"~~~~~~~~~~~~~~~"<<endl;
                cout<<"Please enter a new price : ";
                cin>>temp->flower_price;
                cout << "Flower Price updated successfully." << endl;

                cout<<"\nYou are done, Manager ! If you want to continue to use program press [y / Y] : ";
                cin>>continuee;
                cout<<"\n"<<endl;
            }

            else
            {
                cout << "Invalid flower code. Please try again." << endl;
                cout<<"\nIf you want to continue to use program press[Y/y] : ";
                cin>>continuee;
                cout<<"\n"<<endl;
            }

        }
        
     
		void generate_sales()
		{
            // Create a copy of the original linked list
            Flower *copyHead = nullptr, *copyTemp = nullptr;
            temp = head;
            while (temp != nullptr)
            {
                if (copyHead == nullptr)
                {
                    copyHead = new Flower(*temp);
                    copyTemp = copyHead;
                }
                else
                {
                    copyTemp->next = new Flower(*temp);
                    copyTemp = copyTemp->next;
                }
                temp = temp->next;
            }

            // Sort the copied linked list
            Flower *sortedHead = nullptr;
            Flower *current = copyHead;

            while (current != nullptr)
            {
                Flower *next = current->next;

                if (sortedHead == nullptr || current->flower_default_sales >= sortedHead->flower_default_sales)
                {
                    current->next = sortedHead;
                    sortedHead = current;
                }
                else
                {
                    Flower *temp = sortedHead;
                    while (temp->next != nullptr && temp->next->flower_default_sales > current->flower_default_sales)
                    {
                        temp = temp->next;
                    }
                    current->next = temp->next;
                    temp->next = current;
                }

                current = next;
            }

            // Generate the sales report
            cout << "------------------- Sales Report for this week ( sorted by top sales )-------------------" << endl;
            cout << "Code\tFlower Name\t\tPrice\tSales\tTotal Sales Amount (RM)" << endl;

            float totalEarnings = 0.0; 

            Flower *tempSorted = sortedHead;

           while (tempSorted != nullptr)
            {
               float totalSalesAmount = tempSorted->flower_default_sales * tempSorted->flower_price;
				totalEarnings += totalSalesAmount; 
				cout << left << setw(8) << tempSorted->flower_code << setw(24) << tempSorted->flower_name << fixed << setprecision(2)
                    << setw(8) << tempSorted->flower_price << setw(8) << tempSorted->flower_default_sales << totalSalesAmount << endl;
				tempSorted = tempSorted->next;
            }

            cout << "-----------------------------------------------------------------------" << endl;
            cout << "Total Earnings: RM " << fixed << setprecision(2) << totalEarnings << endl;

            cout << "\nYou are done, Manager! If you want to continue using the program, press [y / Y] : ";
            cin >> continuee;
            cout << "\n" << endl;
			
		}

        Flower* get_head()
        {
            return head;
        }

        Flower* get_temp()
        {
            return temp;
        }
			
}M;

class Customer{
	private:
    string cus_name;
    Flower *head = M.get_head();
    Flower *temp = M.get_temp();
    
    flowerCart *cartHead;
	
	public:
    Customer()
	{
		cartHead=nullptr;
    }
	void customer_info()
    {
		cin.sync();
		cout << "\n";
		cout <<"--------------------------- Enter Your Details ----------------------------"<<endl; 
		cout << "Please enter your name       : ";
        getline(cin, cus_name);
		cout << "\n";
    }
	
	void order()
	{	
        string custOrder;
        char choice1, choice2;
        int quantity;
        int totalQty = 0;
        string shopCart;
        char arrangmentChoice = 'N';  
        string agmType = "NONE";
        float agmPrice = 0.00;
        char wishChoice = 'N';  
        string wishType = "NONE";
        float wishPrice = 0.00;
        char sortchoice;

        menu(temp,head);		
		cout<<"\nGet add-on options when buying 5 or more flowers"<<endl; 
        do{
            cout<<"\nDo you wish to sort? [Y/N]: ";
		    cin>>sortchoice;
            
            if(sortchoice == 'Y' || sortchoice == 'y')
            {
                int userSorting;
		        cout<<"\nChoose sorting category:"<<endl;
		        cout<<"1. Top Sales"<<endl;
		        cout<<"2. Price Low to High"<<endl;
		        cout<<"3. Price High to Low"<<endl;
		        cout<<"4. Alphabetically A-Z"<<endl;
		        cout<<"5. Alphabetically Z-A"<<endl;
		        do{
                    cout<<"\nEnter your choice: ";
		            cin>>userSorting; 

		            switch (userSorting) 
		            {
			            case 1: sortFlowersTopSales();
						          break;
			
			            case 2: sortFlowersByPriceLowToHigh();
						            break;

			            case 3: sortFlowersByPriceHighToLow();
						            break;

			            case 4: sortFlowersAZ();
						            break;

			            case 5: sortFlowersZA();
						            break;
			
			            default: cout<<"Invalid sorting option."<<endl;
					                break;
		            }
                }while(userSorting != 1 && userSorting != 2 && userSorting != 3 && userSorting != 4 && userSorting != 5);
            }

            else if (sortchoice == 'N' || sortchoice == 'n') 
            {
                break; // Exit the loop if 'N' or 'n' is entered
            }

            else
            {
                cout << "Invalid input. Please enter 'Y', 'y', 'N', or 'n'." << endl;
            }
        }while(sortchoice != 'Y' && sortchoice != 'y'&& sortchoice != 'N' && sortchoice != 'n');

        do
        {
			
            cout << "\nWhich flowers would you like to buy?" << endl;
            cout << "Enter code: ";
            cin>>custOrder;

            temp = head;
            while ((temp != NULL) && (temp->flower_code != custOrder)) 
            {
                temp = temp->next;
            }

            if (temp!=NULL && temp->flower_code == custOrder) 
			{
                cout << "How many would you like to buy?: ";
                cin >> quantity;
               
				addToCart(temp, quantity); // send it to the linked list to store customer's order
				temp->flower_default_sales = temp->flower_default_sales + quantity;
                totalQty += quantity;
            } 
			else 
			{
                cout << "\nThe flower code you have entered does not exist!" << endl;
            }

            cout << "\nWould you like to continue shop for more flowers? [Y/N]: ";
            cin >> choice1;
            cin.ignore();

        } while (choice1 == 'Y' || choice1 == 'y');
		
        if (totalQty >= 5)
		{ // This will only display if user buy 5 or more flowers
            cout << "\nWould you like to do an arrangement for your flowers? [Y/N]: ";
            cin >> arrangmentChoice;

            if (arrangmentChoice == 'Y' || arrangmentChoice == 'y') 
			{
                cout << "\nFlower Arrangements" << endl;
                cout << "\nA. Hand-Tied Bouquet (RM10)\nB. Basket Arrangement (RM15)" << endl;
                cout << "\nPick your choice of arrangement: ";
                cin >> arrangmentChoice;

                switch (arrangmentChoice) 
				{
                    case 'A':
                        agmType = "Hand-Tied Bouquet (RM10)";
                        agmPrice = 10.00;
                        break;
                    case 'B':
                        agmType = "Basket Arrangement (RM15)";
                        agmPrice = 15.00;
                        break;
                }
            }

            cout << "\nWould you like to buy a wish card? [Y/N]: ";
            cin >> choice2;

            if (choice2 == 'Y' || choice2 == 'y')
			{
                cout << "\nWish Card" << endl;
                cout << "\nA. Birthday Wish Card\nB. Congratulation Messages\nC. Condolence Card\nD. Anniversary Card\n";
                cout << "\nPick your desired wish card: ";
                cin >> wishChoice;

                switch (wishChoice) 
				{
                    case 'A':
                        wishType = "Birthday Wish Card (RM0.50)";
                        wishPrice = 0.50;
                        break;
                    case 'B':
                        wishType = "Congratulation Message (RM0.50)";
                        wishPrice = 0.50;
                        break;
                    case 'C':
                        wishType = "Condolence Card (RM0.50)";
                        wishPrice = 0.50;
                        break;
                    case 'D':
                        wishType = "Anniversary Card (RM0.50)";
                        wishPrice = 0.50;
                        break;
                }
            }

        }
		
		float total = Calculation(agmPrice, wishPrice);

		Receipt(totalQty, total, agmType, wishType);
    }
        //Selection Sort
	    void sortFlowersByPriceLowToHigh() 
    {
        Flower* current = head;

        while (current != nullptr) 
        {
            Flower* minNode = current;
            Flower* temp = current->next;

            while (temp != nullptr) 
            {
                if (temp->flower_price < minNode->flower_price) 
                {
                    minNode = temp;
                }
                temp = temp->next;
            }

            // Swap the flowers
            swapFlowers(current, minNode);

            current = current->next;
        }

        // Display the sorted flowers after sorting
        displaySortedFlowers("Low to High");
    }

    void sortFlowersByPriceHighToLow() 
    {
        Flower* current = head;

        while (current != nullptr) 
        {
            Flower* maxNode = current;
            Flower* temp = current->next;

            while (temp != nullptr) 
            {
                if (temp->flower_price > maxNode->flower_price) 
                {
                    maxNode = temp;
                }
            temp = temp->next;
            }

            // Swap the flowers
            swapFlowers(current, maxNode);

            current = current->next;
        }

        // Display the sorted flowers after sorting
        displaySortedFlowers("High to Low");
    }

    void sortFlowersTopSales() 
    {
        Flower* current = head;

        while (current != nullptr) 
        {
            Flower* maxNode = current;
            Flower* temp = current->next;

            while (temp != nullptr) 
            {
                if (temp->flower_default_sales > maxNode->flower_default_sales) 
                {
                    maxNode = temp;
                }
                temp = temp->next;
            }

            // Swap the flowers
            swapFlowers(current, maxNode);

            current = current->next;
        }

        // Display the sorted flowers after sorting
        displaySortedFlowers("Top Sales");
    }

    void sortFlowersAZ() 
    {
        Flower* current = head;

        while (current != nullptr) 
        {
            Flower* minNode = current;
            Flower* temp = current->next;

            while (temp != nullptr) 
            {
                if (temp->flower_name < minNode->flower_name) 
                {
                    minNode = temp;
                }
                temp = temp->next;
            }

            // Swap the flowers
            swapFlowers(current, minNode);

            current = current->next;
        }

        // Display the sorted flowers after sorting
        displaySortedFlowers("Alphabetically A-Z");
    }

    void sortFlowersZA() 
    {
        Flower* current = head;

        while (current != nullptr) 
        {
            Flower* maxNode = current;
            Flower* temp = current->next;

            while (temp != nullptr) 
            {
                if (temp->flower_name > maxNode->flower_name) 
                {
                    maxNode = temp;
                }
                temp = temp->next;
            }

            // Swap the flowers
            swapFlowers(current, maxNode);

            current = current->next;
        }

        // Display the sorted flowers after sorting
        displaySortedFlowers("Alphabetically Z-A");
    }


    void swapFlowers(Flower* flower1, Flower* flower2) 
    {
        Flower temp = *flower1;
        flower1->flower_code = flower2->flower_code;
        flower1->flower_name = flower2->flower_name;
        flower1->flower_price = flower2->flower_price;
        flower1->flower_default_sales = flower2->flower_default_sales;
        flower2->flower_code = temp.flower_code;
        flower2->flower_name = temp.flower_name;
        flower2->flower_price = temp.flower_price;
        flower2->flower_default_sales = temp.flower_default_sales;
    }

    void displaySortedFlowers(const string& order) 
    {
        cout << "\n====================== Sorted Flowers by " << order << " ======================" << endl;
        cout << left << setw(10) << "Code" << setw(35) << "Flowers \t \t \t \t \t \t Price (RM)" << endl;
        cout << "---------------------------------------------------------------------------" << endl;

        Flower* tempSorted = head;
        while (tempSorted != NULL) 
        {
            cout << setw(10) << tempSorted->flower_code << setw(35) << tempSorted->flower_name << fixed << setprecision(2) << setw(18) <<"\t"<< tempSorted->flower_price << endl;
            tempSorted = tempSorted->next;
        }

        cout << "----------------------------------------------------------------------------" << endl;
    }
    
	void addToCart(Flower *temp, int quantity) 
	{
		flowerCart* cartTemp = cartHead;
		
		// Check if the flower is already in the cart
		while (cartTemp != nullptr) 
		{
			if (cartTemp->cartFcode == temp->flower_code)
			{
				cartTemp->cartFqty += quantity; // If found, it updates the quantity
				return;
			}
			cartTemp = cartTemp->next;
		}

		// If not found, create a new cart
		flowerCart* cart = new flowerCart;
		cart->cartFcode = temp->flower_code;
		cart->cartFname = temp->flower_name;
		cart->cartFprice = temp->flower_price;
		cart->cartFqty = quantity;
		cart->next = nullptr;

		if (cartHead == nullptr)
		{
			cartHead = cart;
		} 
		else
		{
			cartTemp = cartHead;
			while (cartTemp->next != nullptr) 
			{
				cartTemp = cartTemp->next;
			}
			cartTemp->next = cart;
		}
    }

	float Calculation(float agmPrice, float wishPrice)
	{
		flowerCart *temp;
		temp = cartHead;
		
		int flowerQty;
		float flowerTotalPrice=0.00;
		
		while (temp != nullptr) 
		{
			flowerQty = temp->cartFqty; 
			flowerTotalPrice += temp->cartFprice * flowerQty;
			temp = temp->next;
		}

		return flowerTotalPrice + wishPrice + agmPrice;
		
	}
	
    void Receipt(int totalQty, float total, string agmType, string wishType) 
    {
        cout << "\n\n\n----------------------------------------------------------------------------" << endl;
        cout << "|\t\t\t\t Receipt\t\t\t\t   |" << endl;
        cout << "----------------------------------------------------------------------------" << endl << endl;

        flowerCart* temp = cartHead;
    cout << setw(15) << "Code" << setw(40) << "Flowers" << setw(13) << "Price(RM)" << setw(10) << "Quantity" << endl << endl;

    while (temp != nullptr)
    {
        cout << setw(15) << temp->cartFcode << setw(40) << left << temp->cartFname << fixed << setprecision(2) 
             << setw(13) << temp->cartFprice << setw(10) << temp->cartFqty << endl;
        temp = temp->next;
    }

        cout << "\nArrangement Type = " << agmType << endl;
        cout << "Wish Card = " << wishType << endl;
        cout << "\nTotal: RM " << fixed << setprecision(2) << total << endl;
        cout << "----------------------------------------------------------------------------\n\n\n\n\n\n\n";
	}
};

int main()
{
    char choice;
	int count = 0;
	
	do{
        cout<<"\t\t\tWelcome to our Florist shop!"<<endl;
        cout<<"--------------------------------------------------------------------------"<<endl;
        cout<<"Please select your role:"<<endl;
        cout<<"\tA. Customer"<<endl;
        cout<<"\tB. Manager"<<endl;
        cout<<"Enter your choice (A/B)      : ";
        cin>>choice;
        cout<<"\n";

		if (choice == 'A' || choice == 'a') // if user is customer
        {
            Customer C;			
			C.customer_info();	
			C.order();
        }
        else if (choice == 'B' || choice == 'b') // if user is admin
        {
            
            M.verify(); // verify the password
            continue;
        }
        else
        {
            count++;
            if (count<3) //user maximum can reselect three times
            {
                cout<<"Invalid selection. Please re-select:\n ";
            }
            else
            {
                cout<<"Maximum reselection attempts reached. Exiting program." <<endl;
                break;
            }
        }
    } while (count < 3 && (choice != 'A' || choice != 'a' || choice != 'B' || choice != 'b'));

    return 0;
}

