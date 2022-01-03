# JAVA

### API

- 操作声音文件(.wav)

  ```java
   Clip bgm = AudioSystem.getClip();
   AudioInputStream ais =  AudioSystem.getAudioInputStream(newFile("D:/sound/chooseRole.wav"));
   bgm.open(ais);
   bgm.start();
  ```

- 序列化与反序列化

  ```java
  ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream(文件名称));
  objectOutputStream.writeObject(this);
  ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream(文件名称));
  类型名称 item = (类型名称) objectInputStream.readObject();
  ```

### Swing

- JFrame配置

  ```java
  setUndecorated(true);//去除标题栏和装饰
  Dimension WINDOW = Toolkit.getDefaultToolkit().getScreenSize();//获取界面尺寸
  setLayout(null);//使内层页面可以使用layout
  setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//关闭按钮
  getContentPane().setBackground(Color.black);//设置背景色
  setLocationRelativeTo(null);//居中
  ```

- 滚动条设置

  ```java
  JScrollPane jScrollPane = new JScrollPane(mainPanel,
                  ScrollPaneConstants.VERTICAL_SCROLLBAR_NEVER,
                  ScrollPaneConstants.HORIZONTAL_SCROLLBAR_NEVER);
  jScrollPane.setBounds(50,0,WINDOW.width-100,700);
  ```

- 鼠标拉动屏幕

  ```java
  GraphicsEnvironment env = GraphicsEnvironment.getLocalGraphicsEnvironment();
      GraphicsDevice screen = env.getDefaultScreenDevice();
      Robot robot;
      {
          try {
              robot = new Robot(screen);
          } catch (AWTException e) {
              e.printStackTrace();
          }
      }
  class windowMove extends MouseMotionAdapter {
          @Override
          public void mouseMoved(MouseEvent e) {
              super.mouseMoved(e);
              if(e.getXOnScreen()<=50){
                  robot.mouseMove(50,e.getYOnScreen());
                  jScrollPane.getHorizontalScrollBar().setValue
                          (jScrollPane.getHorizontalScrollBar().getValue()-15);
                  mapPanel.repaint();
              }
              if(e.getXOnScreen()>=WINDOW.width-50){
                  robot.mouseMove(WINDOW.width-50,e.getYOnScreen());
                  jScrollPane.getHorizontalScrollBar().setValue
                          (jScrollPane.getHorizontalScrollBar().getValue()+15);
                  mapPanel.repaint();
              }
              if(e.getYOnScreen()<=20){
                  robot.mouseMove(e.getXOnScreen(),20);
                  jScrollPane.getVerticalScrollBar().setValue
                          (jScrollPane.getVerticalScrollBar().getValue()-15);
                  mapPanel.repaint();
              }
              if(e.getYOnScreen()>=1050){
                  robot.mouseMove(e.getXOnScreen(),1050);
                  jScrollPane.getVerticalScrollBar().setValue
                          (jScrollPane.getVerticalScrollBar().getValue()+15);
                  mapPanel.repaint();
              }
          }
      }
  addMouseMotionListener(new windowMove());
  ```

- 设置全局字体

  ```java
  private static void InitGlobalFont(Font font) {
          FontUIResource fontRes = new FontUIResource(font);
          for (Enumeration<Object> keys = UIManager.getDefaults().keys(); keys.hasMoreElements(); ) {
              Object key = keys.nextElement();
              Object value = UIManager.get(key);
              if (value instanceof FontUIResource) {
                  UIManager.put(key, fontRes);
              }
          }
      }
  ```

- 菜单栏设置

  ```java
  class GameMenu extends JMenuBar{
          public GameMenu(){
              JMenu menu = new JMenu("菜单");
              JMenuItem item = new JMenuItem("保存游戏");
              item.addActionListener(e -> gameSave());
              menu.add(item);
              item = new JMenuItem("重新开始");
              item.addActionListener(e -> {
                  try {
                      FileOutputStream fos = new FileOutputStream(dataFile);
                      fos.write(new byte[0]);
                  } catch (IOException fileNotFoundException) {
                      fileNotFoundException.printStackTrace();
                  }
                  //重置游戏
              });
              menu.add(item);
              item = new JMenuItem("退出游戏");
              item.addActionListener(e -> System.exit(0));
              menu.add(item);
              menu.setBounds(100,0,100,50);
              add(menu);
          }
      }
  ```

  
