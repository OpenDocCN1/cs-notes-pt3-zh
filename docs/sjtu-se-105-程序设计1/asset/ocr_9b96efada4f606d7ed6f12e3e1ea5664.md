# 实例-Library

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