```
class Library{
public:
    vector<Book> books;
    vector<Patron> patrons;
    vector<Transaction> transactions;

    void add_book(Book book){books.push_back(book);}
    void add_patron(Patron patron){patrons.push_back(patron);}
    void borrow_book(Book* book, Patron* patron);
    vector<Patron*> all_bad_guys();
};
```