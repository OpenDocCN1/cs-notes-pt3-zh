# # 数组类模板

#include <iostream.h>
#include "Array.h"
void main()
{ Array <int> IntAry;
for (int i = 0; i < 5; i++) IntAry.Enter (i, i);
cout << "Integer Array : \n" ;
for ( i = 0; i < 5; i++) cout << IntAry.Entry(i) << '\t' ;
cout<<endl ;
Array <double> DouAry( 5 ) ;
for ( i = 0; i < 5; i++) DouAry.Enter (i, (i+1)*0.35 ) ;
cout << "Double Array : \n" ;
for ( i = 0; i < 5; i++)
cout << IntAry.Entry(i) << '\t' ;
cout<<endl;
}

class Array
{
public :
......
virtual const int & Entry( int index ) const ;
virtual void Enter( int index, const int & value ) ;
protected :
int size ; int * element ;
};

class Array
{
public :
......
virtual const double & Entry( int index ) const ;
virtual void Enter( int index, const double & value ) ;
protected :
int size ; double * element ;
};