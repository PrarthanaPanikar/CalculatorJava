# CalculatorJava
import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

public class CalculatorApplet extends Applet implements ActionListener {
    TextField t1, t2, resultField;
    Button Add, sub, mul, div;

    public void init() {
        setLayout(new FlowLayout());

        t1 = new TextField(10);
        t2 = new TextField(10);
        resultField = new TextField(15);
        resultField.setEditable(false);

        Add = new Button("+");
        sub = new Button("-");
        mul = new Button("*");
        div = new Button("/");

        add(new Label("Number 1:")); add(t1);
        add(new Label("Number 2:")); add(t2);
        add(Add); add(sub); add(mul); add(div);
        add(new Label("Result:")); add(resultField);

        Add.addActionListener(this);
        sub.addActionListener(this);
        mul.addActionListener(this);
        div.addActionListener(this);
    }

    public void actionPerformed(ActionEvent e) {
        double num1 = Double.parseDouble(t1.getText());
        double num2 = Double.parseDouble(t2.getText());
        double result = 0;

        if (e.getSource() == Add) {
            result = num1 + num2;
        } else if (e.getSource() == sub) {
            result = num1 - num2;
        } else if (e.getSource() == mul) {
            result = num1 * num2;
        } else if (e.getSource() == div) {
            result = num2 != 0 ? num1 / num2 : 0;
        }

        resultField.setText(String.valueOf(result));
    }
}
