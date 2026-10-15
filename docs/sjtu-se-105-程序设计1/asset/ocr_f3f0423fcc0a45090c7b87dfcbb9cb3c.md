```
// An In_box is a widget into which you can type characters
// It's "action" is to receive characters

struct In_box : Widget {
    In_box(Point xy, int w, int h, const string& s)
        :Widget(xy,w,h,s,0) {}
    int get_int();
    string get_string();
};

int In_box::get_int()
{
    // get a reference to the FLTK FL_Input widget:
    Fl_Input& pi = reference_to<Fl_Input>(pw);
    // use it:
    return atoi(pi.value());      // get the value and convert
                                  // it from characters (alpha) to int
}
```