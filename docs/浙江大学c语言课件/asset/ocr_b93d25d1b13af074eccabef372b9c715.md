# ## 2.4 Declarations

type var1, var2, ..., varN;

int lower, upper, step;
char c, line[1000];

int lower;
int upper;
int step;
char c;
char line[1000];

a variable may also be initialized in its declaration, e.g.;

char esc = '\\';

int i=0;

int limit = MAXLINE +1;

the qualifier const can be appied to the declaration
of any variable to specify that its value will not be changed.

const double e=2.71828;

const char msg[]="warning.";