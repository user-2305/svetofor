# svetofor
Для нарисования светофора в Java, мы будем использовать классы JFrame и JPanel. Класс JFrame используется для создания окна приложения, а JPanel - для рисования графики.

Вот пример кода для нарисования светофора:
```java
import javax.swing.*;
import java.awt.*;

public class TrafficLight extends JPanel {
    private int currentColor = 0;

    public void paintComponent(Graphics g) {
        super.paintComponent(g);

        int width = getWidth();
        int height = getHeight();

        int lightSize = Math.min(width, height) / 3;

        drawLight(g, lightSize, lightSize * 2, Color.RED);
        drawLight(g, lightSize * 2, lightSize, Color.YELLOW);
        drawLight(g, lightSize * 3, lightSize * 2, Color.GREEN);
    }

    private void drawLight(int x, int y, Color color) {
        Graphics2D g2d = (Graphics2D) getGraphics();
        g2d.setColor(color);
        g2d.fillOval(x, y, getWidth() / 3, getHeight() / 3);
        g2d.dispose();
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                JFrame frame = new JFrame("Traffic Light");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                frame.setContentPane(new TrafficLight());
                frame.setSize(300, 300);
                frame.setLocationRelativeTo(null);
                frame.setVisible(true);
            }
        });
    }
}
```
В этом примере мы создаем класс TrafficLight, наследующийся от JPanel. В методе paintComponent мы рисуем светофор из трёх светодиодов: красного, желтого и зелёного цветов. Для каждого светодиода мы определяем координаты и цвет и вызываем метод drawLight для рисования.

В методе main мы создаём окно JFrame и устанавливаем контентом наш класс TrafficLight. Затем устанавливаем размеры окна и делаем его видимым.

Когда этот код будет запущен, окно с светофором будет отображено на экране.
