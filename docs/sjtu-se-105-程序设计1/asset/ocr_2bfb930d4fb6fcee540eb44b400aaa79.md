+   - 支持C风格字符串的Queue
+   ```cpp
+   template <> class Queue<const char*> {
+   public
+       void push(const char*);
+       void pop() {real_queue.pop();}
+       bool empty() const {return real_queue.empty();}
+       // note: return type does not match template para type
+       std::string front() {return real_queue.front();}
+       const std::string front() const {return real_queue.front();}
+   private:
+       Queue<std::string> real_queue; //forward calls to it
+   ```