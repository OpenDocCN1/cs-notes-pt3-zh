```
void print_bad_guys(){
    vector<Patron*> patrons = library.all_bad_guys();
    for(unsigned int i = 0; i<patrons.size();i++)
        cout << (*patrons[i]);
};
```