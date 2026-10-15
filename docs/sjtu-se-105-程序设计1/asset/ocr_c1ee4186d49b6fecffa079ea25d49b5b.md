```
void borrow_books(){
    for(unsigned int i=0; i<library.books.size();i++)
    for(unsigned int j=0; j<library.patrons.size();j++)
        try{
            Book* book = &library.books[i];
            Patron* patron = &library.patrons[j];
            library.borrow_book(book,patron);
        }catch (exception& e) {
            cerr << "error: " << e.what() << '\n';
        }catch (...) {
            cerr << "Oops: unknown exception!\n";
        }
};
```