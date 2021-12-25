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

