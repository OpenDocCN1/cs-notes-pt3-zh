```
struct Lines_window : Window    // Lines_window inherits from Window
{
    Lines_window(Point xy, int w, int h, const string& title); // declare constructor
    Open_polyline lines;

private:
    Button next_button;                // declare some buttons – type Button
    Button quit_button;
    In_box next_x;                     // declare some i/o boxes
    In_box next_y;
    Out_box xy_out;

    void next();                       // what to do when next_button is pushed
    void quit();                       // what to do when quit_button is pushed

    static void cb_next(Address, Address window);    // callback for next_button
    static void cb_quit(Address, Address window);    // callback for quit_button
};
```