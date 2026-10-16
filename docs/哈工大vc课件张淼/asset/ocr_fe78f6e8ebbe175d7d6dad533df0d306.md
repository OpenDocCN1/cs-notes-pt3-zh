```
class Time
{
	public:
	
	Time( int = 0, int = 0, int = 0 );
	void setTime( int, int, int );
	int getHour();
	
	int &badSetHour( int ); // DANGEROUS reference return
	
	private:
	
	int hour;
	int minute;
	int second;
	
}; // end class Time
```