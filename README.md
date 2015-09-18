# Fan
fan that has multiple buttons and reacts to camands
package fan;
 
 /**
 
 *
 
 * @author juan Carpinteiro
 
 *  E-solutions Development. LLC
 
 */
 
 import java.awt.*;
 
 import java.awt.event.ActionEvent;
 
 import java.awt.event.ActionListener;
 
 import javax.swing.*;
 
 public class Fan extends JFrame {
 
    JButton button1 = new JButton("ON");
 
    JButton button2 = new JButton("OFF");
 
    JButton button3 = new JButton("SLOW");
 
    JButton button4 = new JButton("MEDIUM");
 
    JButton button5 = new JButton("FAST");
 
    JButton button6 = new JButton("REVERSE");
 
    Timer t;
 
    int disp;
 
    int speed=1;
 
    Blades blades;
 
    Fan() {
 
        setLayout(new BorderLayout());
 
        blades = new Blades();
 
        JPanel controls = new JPanel();
 
        controls.setLayout(new FlowLayout(FlowLayout.LEFT, 10, 10));
 
        controls.add(button1);
 
        button1.addActionListener(new BtnListener());
 
        controls.add(button2);
 
        button2.addActionListener(new BtnListener());
 
        
 
        controls.add(button3);
 
        button3.addActionListener(new BtnListener());
 
        controls.add(button4);
 
        button4.addActionListener(new BtnListener());
 
        controls.add(button5);
 
        button5.addActionListener(new BtnListener());
 
        
 
        controls.add(button6);
 
        button6.addActionListener(new BtnListener());
 
        
 
        add(blades, BorderLayout.CENTER);
 
        add(controls, BorderLayout.SOUTH);
 
        t = new Timer(100, new TimerListener());
 
    }
 
    public static void main(String[] args) {
 
        Fan fan = new Fan();
 
        fan.setTitle("NYCCT Fan");
 
        fan.setSize(500, 500);
 
        fan.setLocationRelativeTo(null);
 
        fan.setDefaultCloseOperation(EXIT_ON_CLOSE);
 
        fan.setVisible(true);
 
        // TODO code application logic here
 
    }
 
    class Blades extends JPanel {
 
        
 
        protected void paintComponent(Graphics g) {
 
            super.paintComponent(g);
 
            int noOfBlades = 6;
 
            int h = getHeight();
 
            int w = getWidth();
 
            g.setColor(Color.BLUE);
 
            g.drawOval(20, 20, w - 40, h - 40);
 
            g.setColor(Color.RED);
 
            for (int i = 0; i < noOfBlades; i++) {
 
                g.fillArc(20, 20, w - 40, h - 40, (int) (( i * 360./ noOfBlades +(disp*speed) )), (int)  (360. / (noOfBlades * 3)));
 
            }
 
        }
 
    }
 
    class TimerListener implements ActionListener {
 
        @Override
 
        public void actionPerformed(ActionEvent e) {
 
            
 
               disp= disp+2;
 
                blades.repaint();
 
            
 
        }
 
    }
 
    class BtnListener implements ActionListener
 
    {
 
        @Override
 
        public void actionPerformed(ActionEvent e) {
 
          if(e.getSource()==button1){
 
                 t.start();
 
                 speed=3;
 
          }
 
          else if (e.getSource()==button2){
 
              t.stop();
 
          }
 
          else if (e.getSource()==button3){
 
              speed=1;
 
          }
 
          else if (e.getSource()==button4){
 
              speed=3;
 
          }
 
            else if (e.getSource()==button5){
 
              speed=6;
 
          }
 
          else if (e.getSource()==button6){
 
              speed=speed-6;
 
          }
 
           
 
        }
 
        
 
    }
 
 }
 
