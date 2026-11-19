# library-management-system.
import java.util.Scanner;

class LibraryManagementSystem
{
    static Scanner sc = new Scanner(System.in);

    static int[] bookId = new int[100];
    static String[] bookName = new String[100];
    static String[] author = new String[100];
    static boolean[] issued = new boolean[100];

    static int count = 0;

    public static void addBook()
    {
        System.out.print("Enter Book ID: ");
        bookId[count] = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Book Name: ");
        bookName[count] = sc.nextLine();

        System.out.print("Enter Author Name: ");
        author[count] = sc.nextLine();

        issued[count] = false;
        count++;

        System.out.println("Book Added Successfully!");
    }

    public static void viewBooks()
    {
        if(count == 0)
        {
            System.out.println("No Books Available.");
            return;
        }

        for(int i = 0; i < count; i++)
        {
            System.out.println("Book ID: " + bookId[i]);
            System.out.println("Book Name: " + bookName[i]);
            System.out.println("Author: " + author[i]);
            System.out.println("Status: " +
                (issued[i] ? "Issued" : "Available"));
            System.out.println("----------------------");
        }
    }

    public static void searchBook()
    {
        System.out.print("Enter Book ID: ");
        int id = sc.nextInt();

        for(int i = 0; i < count; i++)
        {
            if(bookId[i] == id)
            {
                System.out.println("Book Found!");
                System.out.println("Book Name: " + bookName[i]);
                System.out.println("Author: " + author[i]);
                return;
            }
        }

        System.out.println("Book Not Found!");
    }

    public static void issueBook()
    {
        System.out.print("Enter Book ID: ");
        int id = sc.nextInt();

        for(int i = 0; i < count; i++)
        {
            if(bookId[i] == id)
            {
                if(!issued[i])
                {
                    issued[i] = true;
                    System.out.println("Book Issued Successfully!");
                }
                else
                {
                    System.out.println("Book Already Issued!");
                }
                return;
            }
        }

        System.out.println("Book Not Found!");
    }

    public static void returnBook()
    {
        System.out.print("Enter Book ID: ");
        int id = sc.nextInt();

        for(int i = 0; i < count; i++)
        {
            if(bookId[i] == id)
            {
                if(issued[i])
                {
                    issued[i] = false;
                    System.out.println("Book Returned Successfully!");
                }
                else
                {
                    System.out.println("Book Was Not Issued!");
                }
                return;
            }
        }

        System.out.println("Book Not Found!");
    }

    public static void main(String args[])
    {
        int choice;

        do
        {
            System.out.println("\n--- LIBRARY MANAGEMENT SYSTEM ---");
            System.out.println("1. Add Book");
            System.out.println("2. View Books");
            System.out.println("3. Search Book");
            System.out.println("4. Issue Book");
            System.out.println("5. Return Book");
            System.out.println("6. Exit");

            System.out.print("Enter Your Choice: ");
            choice = sc.nextInt();

            switch(choice)
            {
                case 1:
                    addBook();
                    break;

                case 2:
                    viewBooks();
                    break;

                case 3:
                    searchBook();
                    break;

                case 4:
                    issueBook();
                    break;

                case 5:
                    returnBook();
                    break;

                case 6:
                    System.out.println("Thank You!");
                    break;

                default:
                    System.out.println("Invalid Choice!");
            }

        } while(choice != 6);
    }
}
