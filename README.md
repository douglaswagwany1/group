# grou
# Employee class
class Employee:
    def __init__(self, emp_id, name, department):
        self.emp_id = emp_id
        self.name = name
        self.department = department

    def display(self):
        print("ID:", self.emp_id,
              "| Name:", self.name,
              "| Department:", self.department)


# Node class for Binary Search Tree
class Node:
    def __init__(self, employee):
        self.employee = employee
        self.left = None
        self.right = None


# Employee Management System
class EmployeeManagementSystem:
    def __init__(self):
        self.root = None

    # Insert employee into BST
    def insert(self, employee):
        new_node = Node(employee)

        if self.root is None:
            self.root = new_node
            return

        current = self.root

        while True:
            if employee.emp_id < current.employee.emp_id:
                if current.left is None:
                    current.left = new_node
                    return
                current = current.left

            elif employee.emp_id > current.employee.emp_id:
                if current.right is None:
                    current.right = new_node
                    return
                current = current.right

            else:
                print("Employee ID already exists!")
                return

    # Search employee using ID
    def search(self, emp_id):
        current = self.root

        while current is not None:
            if emp_id == current.employee.emp_id:
                return current.employee

            elif emp_id < current.employee.emp_id:
                current = current.left

            else:
                current = current.right

        return None

    # Inorder traversal (ascending order)
    def inorder(self, node):
        if node is not None:
            self.inorder(node.left)
            node.employee.display()
            self.inorder(node.right)

    # Find employee with smallest ID
    def find_smallest(self):
        if self.root is None:
            return None

        current = self.root

        while current.left is not None:
            current = current.left

        return current.employee

    # Find employee with largest ID
    def find_largest(self):
        if self.root is None:
            return None

        current = self.root

        while current.right is not None:
            current = current.right

        return current.employee


# MAIN PROGRAM
system = EmployeeManagementSystem()

# Create at least seven employees
employees = [
    Employee(105, "John", "IT"),
    Employee(102, "Mary", "Finance"),
    Employee(108, "Peter", "HR"),
    Employee(101, "Sarah", "IT"),
    Employee(104, "David", "Marketing"),
    Employee(110, "Grace", "Finance"),
    Employee(103, "James", "HR")
]

# Insert employees
for employee in employees:
    system.insert(employee)

# Display employees in ascending order
print("\nEMPLOYEES IN ASCENDING ORDER:")
system.inorder(system.root)

# Search employee
print("\nSEARCH EMPLOYEE:")
result = system.search(104)

if result:
    result.display()
else:
    print("Employee not found!")

# Smallest employee ID
print("\nEMPLOYEE WITH SMALLEST ID:")
smallest = system.find_smallest()

if smallest:
    smallest.display()

# Largest employee ID
print("\nEMPLOYEE WITH LARGEST ID:")
largest = system.find_largest()

if largest:
    largest.display()

p
