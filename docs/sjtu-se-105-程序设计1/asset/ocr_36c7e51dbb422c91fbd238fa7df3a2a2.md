```
template <>
void Queue<const char*>::push(const char* const &val){
    char* new_item = new char[strlen(val)-1];
    strncpy(new_item, val, strlen(val)+1);
    QueueItem<const char*>* pt =
        new QueueItem<const char*>(new_item);
    if (empty())
        head = tail = pt;
    else{
        tail->next = pt;
        tail = pt;
    }
}
```