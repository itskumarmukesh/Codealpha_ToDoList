# Codealpha_ToDoList
Here i am sharing Console-Based To-Do List Application for organizing your tasks.

A simple console-based to-do list application to help you manage your tasks efficiently from the command line.
## Features{
- **Add Tasks**: Easily add new tasks to your to-do list.
- **View Tasks**: Display all your tasks in a clear list format.
- **Mark Tasks as Complete**: Mark tasks as done once you've completed them.
- **Delete Tasks**: Remove tasks you no longer need.
- **Persistent Storage**: Save your tasks between sessions.}

- CODE FOR THE APPLICATION:-

#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Task 
{
public:
    string description;
    bool completed;
    Task(string desc) : description(desc), completed(false) {}
};

class ToDo 
{ 
private:
    vector<Task> tasks;
public: 
    void addTask(const string &task) 
    {
        tasks.emplace_back(task);
    }
    void completeTask(int index) 
    {
        if (index >= 0 && index < tasks.size()) 
        {
            tasks[index].completed = true;
        } 
        else 
        {
            cout << "Invalid task number" << endl;
        }
    }

    void viewTasks() const 
    {
        for (size_t i = 0; i < tasks.size(); ++i) 
        {
            cout << i + 1 << ". " << tasks[i].description
                 << " - " << (tasks[i].completed ? "Completed" : "Not Completed") << endl;
        }
    }
};

void displayMenu() 
{
    cout << "Console Based To-Do List Application: " << endl;
    cout << "1. Add a task" << endl;
    cout << "2. Mark your task as completed" << endl;
    cout << "3. View tasks" << endl;
    cout << "4. Exit" << endl;
}

int main() 
{
    ToDo todoList;
    int choice;

    while (true) 
    {
        displayMenu();
        cout << "Choose an option: ";
        cin >> choice;
        //we will ignore newline character
        cin.ignore(); 

        if (choice == 1) 
        {
            string task;
            cout << "Please enter the task: ";
            getline(cin, task);
            todoList.addTask(task);
            cout << "Task successfully added." << endl;
        } 
        else if (choice == 2) 
        {
            todoList.viewTasks();
            int taskNum;
            cout << "Please enter the number of the task to mark as completed: ";
            cin >> taskNum;
            //we will ignore newline character 
            cin.ignore(); 
            todoList.completeTask(taskNum - 1);
            cout << "Your task successfully marked as completed." << endl;
        }
         else if (choice == 3) 
         {
            todoList.viewTasks();
        } 
        else if (choice == 4) 
        {
            cout << "Exiting the application." << endl;
            break;
        } 
        else 
        {
            cout << "Invalid choice. Try again." << endl;
        }
    } 

    return 0;
};
