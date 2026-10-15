+   - Table per class strategy

```
@WebServlet("/FruitServlet")
public class FruitServlet extends HttpServlet {
    protected void processRequest(HttpServletRequest request,
                                 HttpServletResponse response)
        throws ServletException, IOException {
        ....
        List fruits = session.createQuery("from Fruit").list();
        session.getTransaction().commit();

        for (int i = 0; i < fruits.size(); i++) {
            Fruit theFruit = (Fruit)fruits.get(i);
            out.println("id: " + theFruit.getUid() + "<br>" +
            ....
            if (theFruit instanceof Apple) {
                Apple aFruit = (Apple)theFruit;
                out.println("weight: " + aFruit.getWeight() + "<br>");
            }
        }
    }
}
```