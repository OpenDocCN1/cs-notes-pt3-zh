# # Other cctype functions

int isdigit ( char c ); // 0-9
int isalpha ( char c ); // a-z, A-Z
int isspace ( char c ); // \n, \t, space
int islower ( char c ); // a-z
int isupper ( char c ); // A-Z
....and others

int toupper( char c ); // a ⇒ A
int tolower( char c ); // A ⇒ a

ch = toupper( ch ); // no problem
cout << toupper( 'a' ) // ! problem !