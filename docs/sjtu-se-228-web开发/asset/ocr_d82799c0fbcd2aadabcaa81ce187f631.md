```
public class UserManagerServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
    public UserManagerServlet() {
        super();
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        try {
            HibernateUtil.getSessionFactory().
                getCurrentSession().beginTransaction();
            PrintWriter out = response.getWriter();
            out.println("<html><head><title>
                User Manager</title></head><body>");
            listUser(out);

            out.println("</body></html>");
            out.flush();
            out.close();
            HibernateUtil.getSessionFactory().
                getCurrentSession().getTransaction().commit();
        }
    }
```