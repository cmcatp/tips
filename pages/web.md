# WEB

## html



## css

- tr,td,table边界线重叠

  ```
  解决方法:设置table的CSS为{border-collapse:collapse;border:none;},再设置td的CSS为{border:solid #000 1px;}
  ```

- 组件居中

  ```
  text-align:内容居中,margin:0 auto:自身水平居中
  ```

  

### javascript

- 时间转换

  ```js
  let d = time == null ? new Date() : new Date(time)
  let str = '';
  str += d.getFullYear() + '年'; 
  str += d.getMonth() + 1 + '月'; 
  str += d.getDate() + '日';
  str += d.getHours() + '时';
  str += d.getMinutes() + '分';
  str += d.getSeconds() + '秒';
  ```

- 文件操作

  ```js
  let file = document.getElementById("file").files[0]
  let reader = new FileReader();
  reader.readAsText(file, "UTF-8");
  reader.onload = function (evt) {
  	let fileContent = evt.target.result;
  }
  ```

  