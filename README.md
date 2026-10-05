# Employee Management System

A Windows console employee manager written in C++, with employee CRUD operations, search by ID/name/role, arrow-key menus, and text-file persistence.

## Features

- Add, view, update, and delete employees.
- Search by employee ID, name, or role.
- Store each employee's ID, name, and role in `employees.txt`.
- Register or log in with a local demo account stored in `login.txt`.
- Navigate the main menu with the keyboard.

## Requirements

Use **Windows** with Git and a MinGW-w64/MSYS2-compatible `g++` compiler. The source uses `conio.h`, `getch`/`_getch`, and `system("cls")`, so it is not currently a portable Linux/macOS console application. No package manager or external application framework is required.

## Clone, build, and run

Open PowerShell in a directory where you want the project:

```powershell
git clone https://github.com/PANHARO/employee-management-system.git
cd employee-management-system
g++ --version
g++ -std=c++17 -x c++ .\main.c++ -o .\employee-management.exe
.\employee-management.exe
```

Build from source rather than relying on the executable files already in the repository. Run the new executable from the repository root because the data files are resolved relative to the working directory.

## Using the program

1. At the first screen, use the numbered options to log in or register.
2. Choose **Register** to create your own demo account. Registration replaces the existing login record; this is a single stored account, not a multi-user system.
3. Use Up/Down arrows and Enter to select the main-menu action. Use Esc where offered to return or exit.
4. Add an employee with an unused ID. The add operation also checks for a role already used by another employee.
5. Search, update, or delete records as needed. Changes are written to `employees.txt`.

Use fictional data and a demo password. Login details are stored as plain text. Back up `employees.txt` before editing or deleting records you want to keep.

## Project structure

| Path | Purpose |
| --- | --- |
| `main.c++` | Entry point, initial data loading, and login |
| `model/employee.hpp` | Employee model |
| `repository/employee_repo.hpp` | In-memory employee collection |
| `service/employee_service.hpp` | CRUD, search, login, and file persistence |
| `view/UI.hpp` | Console menus |
| `view/table.hpp` | Table display helpers |
| `employees.txt` | Employee records: ID, name, and role on consecutive lines |
| `login.txt` | One stored username and password |

## Portability and troubleshooting

- If `g++` is not recognized, add your compiler's binary directory to PATH or use its configured terminal.
- `main.c++` includes `view/ui.hpp`, while the file is named `view/UI.hpp`. Windows usually resolves that case difference; a case-sensitive filesystem requires correcting the include.
- Console input and screen clearing need replacements for Linux/macOS. The `strcasecmp` call also depends on compiler support; MSVC may require a different function.
- Input validation and authentication are intended for coursework, not a production HR system.

For changes, fork the repository if necessary and use a separate branch. Include your compiler and operating system when reporting a build issue or proposing a contribution. Avoid committing generated executables or private employee/login data.
