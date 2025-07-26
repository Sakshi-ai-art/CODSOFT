# Start with an empty list
todo_list = []

# Function to show the menu
def show_menu():
    print("\n--- TO-DO LIST MENU ---")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Mark Task as Done")
    print("4. Delete Task")
    print("5. Exit")

# Function to view all tasks
def view_tasks():
    if not todo_list:
        print("No tasks added yet.")
    else:
        for i, task in enumerate(todo_list):
            status = "Done" if task["done"] else "Not Done"
            print(f"{i+1}. {task['name']} - {status}")

# Function to add a task
def add_task():
    name = input("Enter task name: ")
    todo_list.append({"name": name, "done": False})
    print("Task added.")

# Function to mark a task as done
def mark_task_done():
    view_tasks()
    num = int(input("Enter task number to mark as done: ")) - 1
    if 0 <= num < len(todo_list):
        todo_list[num]["done"] = True
        print("Task marked as done.")
    else:
        print("Invalid number.")

# Function to delete a task
def delete_task():
    view_tasks()
    num = int(input("Enter task number to delete: ")) - 1
    if 0 <= num < len(todo_list):
        removed = todo_list.pop(num)
        print(f"Deleted: {removed['name']}")
    else:
        print("Invalid number.")

# Main program loop
while True:
    show_menu()
    choice = input("Choose 1 to 5: ")

    if choice == "1":
        view_tasks()
    elif choice == "2":
        add_task()
    elif choice == "3":
        mark_task_done()
    elif choice == "4":
        delete_task()
    elif choice == "5":
        print("Goodbye!")
        break
    else:
        print("Invalid option. Try again.")
