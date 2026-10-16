```
void Polynomial::NewTerm(const float theCoeff, const int theExp)
{ // add a new term to the end of termArray.
    if (terms == capacity)
    { // double capacity of termArray
        capacity *= 2;
        term *temp = new term[capacity]; // new array
        copy(termArray, termAarry + terms, temp);
        delete [] termArray; // deallocate old memory
        termArray = temp;
    }
    termArray[terms].coef = theCoeff;
    termArray[terms++].exp = theExp;
}
```