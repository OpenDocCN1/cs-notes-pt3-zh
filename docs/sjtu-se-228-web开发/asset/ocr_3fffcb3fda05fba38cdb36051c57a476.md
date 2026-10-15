# Associating Objects with a Session

+   - You can associate object-valued attributes with a session by name.
+     - Such attributes are accessible by any web component that belongs to the same web context and is handling a request that is part of the same session.

```
HttpSession hs = request.getSession();
Shoppingcart cart = new Shoppingcart();
hs.setAttribute("cart", cart);
cart.add(item);
```

```
HttpSession hs = request.getSession();
Shoppingcart cart = hs.getAttribute("cart");
List<Object> ls = cart.getItems();
```