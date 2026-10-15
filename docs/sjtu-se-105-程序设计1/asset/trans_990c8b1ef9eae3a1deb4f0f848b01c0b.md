

- 创建一个 Library 类。
  - 包含 Books 和 Patrons 的向量。
  - 包含一个名为 Transaction 的结构体。
    - 让它包含一个 Book、一个 Patron 和一个 Date
  - 创建一个 Transactions 的向量。
  - 创建向图书馆添加书籍、向图书馆添加读者以及检查所有书籍的函数。
- 每当用户借阅一本书时，让图书馆确保该用户和该书都在图书馆中。
  - 如果不在，则报告错误。
  - 然后检查用户是否未欠费。
  - 如果用户欠费，则报告错误。如果没有，则创建 Transaction，并将其放入 Transactions 向量中。
  - 还创建一个方法，该方法将返回一个包含所有欠费读者的姓名的向量。

```
struct Transaction{
    Book* book;
    Patron* patron;
    Date date;
    Transaction(Book* bb, Patron* pp, Date dd): book(bb), patron(pp), date(dd){};
};
```

```
ostream& operator<<(ostream& os, Transaction& t){
    cout <<"Transaction:" <<endl;
    cout << (*t.book) << " is borrowed by" << (*t.patron);
    return os;
};
```

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

```
void Library::borrow_book(Book* book, Patron* patron){
    unsigned int i;
    for (i = 0; i<books.size(); i++)
        if ((*book)==books[i]) break;
    if (i==books.size()) error("No such a book! ");

    for (i = 0; i<patrons.size(); i++)
        if ((*patron)==patrons[i]) break;
    if (i==patrons.size()) error("No such a patron! ");

    if ((*patron).get_owing()<0) error("You owe me money!");

    Transaction* transaction = new Transaction (book, patron, Date());
    transactions.push_back(*transaction);
    cout << (*transaction);
};
```

```
vector<Patron*> Library::all_bad_guys(){
    vector<Patron*> bad_guys;
    for (unsigned int i = 0; i<patrons.size(); i++)
        if (patrons[i].get_owing()<0)
    bad_guys.push_back(&patrons[i]);
    return bad_guys;
};
```

Library library;

- void input_books();
- void check_same_books();
- void input_patrons();
- void check_same_patrons();
- void print_bad_guys()

```
void input_books(){
    char c;
    string isbn;
    string title;
    string author;
    Date date(27,11,2012);
    int g;
    cout<<"Input Books:"<<endl;
    while((cin>>c) &&(c!='q')){
        try{
            cin >> isbn >> title >>author>>g;
            Book book(isbn,title,author,date,false,Genre(g));
            library.add_book(book);
            cout << book;
        }catch (exception& e) {
            cerr << "error: " << e.what() << '\n';
        }catch (...) {
            cerr << "Oops: unknown exception!\n";
        }
    }
};
```

## 实例-Library

```
void input_patrons(){
    char c;
    string name;
    string number;
    int owing;
    cout<<"Input Patrons:" << endl;
    while((cin>>c) &&(c!='q')){
        try{
            cin >> name >> number >>owing;
            Patron patron(name, number, owing);
            library.add_patron(patron);
            cout << patron;
        }catch (exception& e) {
            cerr << "error: " << e.what() << '\n';
        }catch (...) {
            cerr << "Oops: unknown exception!\n";
        }
    }
};
```

```
void check_same_books(){
    for(unsigned int i = 0; i<books.size();i++)
    for (unsigned int j = i+1; j<books.size();j++){
        if (books[i] == books[j])
        cout<<"Same books: Book" << i << " and Book" << j <<endl;
    }
}

void check_same_patrons(){
    for(unsigned int i = 0; i<patrons.size();i++)
    for (unsigned int j = i+1; j<patrons.size();j++){
        if (patrons[i] == patrons[j])
        cout<<"Same patrons: Patron" << i << " and Patron" << j <<endl;
    }
}
```

