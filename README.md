فاطمه, [⁨30⁩ نوفمبر، ⁨2024⁩ عند ⁨10:00 PM⁩]
public class Book
{
    public string Title { get; set; }
    public string Author { get; set; }
    public bool IsAvailable { get; set; }

    public Book(string title, string author)
    {
        Title = title;
        Author = author;
        IsAvailable = true;
    }

    public void CheckOut()
    {
        IsAvailable = false;
    }

    public void Return()
    {
        IsAvailable = true;
    }
}

public class LibraryCatalog
{
    private List<Book> books;

    public LibraryCatalog()
    {
        books = new List<Book>();
    }

    public void AddBook(string title, string author)
    {
        Book newBook = new Book(title, author);
        books.Add(newBook);
        Console.WriteLine("Book added." + title);
    }

    public void SearchByTitle(string title)
    {
        foreach (Book book in books)
        {
            if (book.Title.Equals(title, StringComparison.OrdinalIgnoreCase))
            {
                Console.WriteLine("I found the book " + book.Title + " By its author: " + book.Author + " ، Available " + book.IsAvailable);
                return;
            }
        }
        Console.WriteLine("No book found for this title.");
    }

    public void SearchByAuthor(string author)
    {
        foreach (Book book in books)
        {
            if (book.Author.Equals(author, StringComparison.OrdinalIgnoreCase))
            {
                Console.WriteLine("I found the book: " + book.Title + " By its author: " + book.Author + " ، Available  " + book.IsAvailable);
            }
        }
    }
}
public class Program
{
    public static void Main(string[] args)
    {
        LibraryCatalog catalog = new LibraryCatalog();
        bool exit = false;

        while (!exit)
        {
            Console.WriteLine("Select the operation : ");
            Console.WriteLine("1.Add Book");
            Console.WriteLine("2.Search for Book by Title");
            Console.WriteLine("3.Search for Book by Author");
            Console.WriteLine("4. Exit");
            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    Console.Write("Enter the book title ");
                    string title = Console.ReadLine();
                    Console.Write("Enter the book author ");
                    string author = Console.ReadLine();
                    catalog.AddBook(title, author);
                    break;

                case "2":
                    Console.Write("Enter the book title to search ");
                    string searchTitle = Console.ReadLine();
                    catalog.SearchByTitle(searchTitle);
                    break;

                case "3":
                    Console.Write("Enter the book author to search ");
                    string searchAuthor = Console.ReadLine();
                    catalog.SearchByAuthor(searchAuthor);
                    break;

                case "4":
                    exit = true;
                    break;

                default:
                    Console.WriteLine(".Invalid options, try again.");
                    break;
