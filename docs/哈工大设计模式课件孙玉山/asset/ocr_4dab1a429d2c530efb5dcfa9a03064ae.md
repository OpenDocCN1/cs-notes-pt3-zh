# Example of design using strategy pattern

```
class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent ae) {
        if (ae.getActionCommand().equals(FIND)) {
            String yr = getYear();
            String mon = getMonth();
            String date = getDate();
            Context context = new Context(yr, mon, date);
            String saying = context.getZodiacDescription();
            ImageIcon icon = context.getImageIcon();
            setImageInfo(icon);
            txtDisplayZodiac.setText("");
            showZodiacInfo(saying);
        }
    }
}
```

这里没有将具体的策略子类的对象传递给Context类