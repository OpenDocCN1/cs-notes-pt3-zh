```
}
char* what() const { return "Woodwind";
}
};

// Identical function from before:
void tune(Instrument& i) {
// ...
i.play(middleC);
}

// New function:
void f(Instrument& i)
{
i.adjust(1);
}

int main()
{
Wind flute;//长笛
Percussion drum;
```