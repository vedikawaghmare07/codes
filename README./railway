#include<iostream>
#include<string>
#include<new>
using namespace std;

struct Node
{
    int passengerID;
    string passengerName;
    Node*next;
};

class CircularQueue
{
private:
    Node*front;
    Node*rear;

public:
    CircularQueue()
    {
        front=NULL;
        rear=NULL;
    }

    bool isEmpty()
    {
        return front==NULL;
    }

    bool isFull()
    {
        Node*temp=new(nothrow)Node;
        if(temp==NULL)
            return true;

        delete temp;
        return false;
    }

    void enqueue(int id,string name)
    {
        if(isFull())
        {
            cout<<"Queue Overflow!Waiting list is full.\n";
            return;
        }

        Node*newNode=new Node;
        newNode->passengerID=id;
        newNode->passengerName=name;

        if(front==NULL)
        {
            front=newNode;
            rear=newNode;
            rear->next=front;
        }
        else
        {
            rear->next=newNode;
            rear=newNode;
            rear->next=front;
        }

        cout<<"Passenger added to waiting list successfully.\n";
    }

    void dequeue()
    {
        if(isEmpty())
        {
            cout<<"Queue Underflow!No passenger in waiting list.\n";
            return;
        }

        Node*temp=front;

        if(front==rear)
        {
            cout<<"Ticket Confirmed for Passenger ID:"<<front->passengerID<<endl;
            cout<<"Passenger Name:"<<front->passengerName<<endl;
            front=NULL;
            rear=NULL;
        }
        else
        {
            cout<<"Ticket Confirmed for Passenger ID:"<<front->passengerID<<endl;
            cout<<"Passenger Name:"<<front->passengerName<<endl;
            front=front->next;
            rear->next=front;
        }

        delete temp;
    }

    void display()
    {
        if(isEmpty())
        {
            cout<<"Waiting list is empty.\n";
            return;
        }

        Node*temp=front;

        cout<<"\nRailWay Waiting List:\n";
        cout<<"PassengerID\tpassengerName\n";

        do
        {
            cout<<temp->passengerID<<"\t\t"<<temp->passengerName<<endl;
            temp=temp->next;
        }while(temp!=front);
    }

    void checkStatus()
    {
        if(isEmpty())
        {
            cout<<"Queue Status:EMPTY\n";
        }
        else if(isFull())
        {
            cout<<"Queue Status:FULL\n";
        }
        else
        {
            cout<<"Queue Status:NOT EMPTY/AVAILABLE\n";
        }
    }
};

int main()
{
    CircularQueue q;
    int choice;
    int id;
    string name;

    do
    {
        cout<<"\n=====RAILWAY RESERVATION SYSTEM=====\n";
        cout<<"1.Add Passenger to Waiting List\n";
        cout<<"2.Confirm Ticket/Remove Passenger\n";
        cout<<"3.Display Waiting List\n";
        cout<<"4.Check Queue Status\n";
        cout<<"5.Exit\n";
        cout<<"Enter your Choice:";
        cin>>choice;

        switch(choice)
        {
            case 1:
                cout<<"Enter Passenger ID:";
                cin>>id;
                cout<<"Enter Passenger Name:";
                cin>>name;
                q.enqueue(id,name);
                break;

            case 2:
                q.dequeue();
                break;

            case 3:
                q.display();
                break;

            case 4:
                q.checkStatus();
                break;

            case 5:
                cout<<"Existing Railway Reservation System.\n";
                break;

            default:
                cout<<"Invalid Choice!Please try again.\n";
        }

    }while(choice!=5);

    return 0;
}
