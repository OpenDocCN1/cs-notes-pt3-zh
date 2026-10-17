```
//Wind管乐器
class Wind : public Instrument {
public:
void play(note) const {
cout << "Wind::play" << endl;
}
char* what() const { return "Wind"; }
void adjust(int) {
cout<< "Wind::adjust" << endl;
}
};
// Percussion 打击乐器
class Percussion : public Instrument {
public:
void play(note) const {
cout << "Percussion::play" << endl;
}
char* what() const { return "Percussion"; }
void adjust(int) {
cout<< "Percussion::adjust" << endl;
}
};
//Stringed弦乐器
```