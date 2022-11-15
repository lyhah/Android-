# Exp_03 Android UI组件

### 1. ListView的用法

- #### 思路

  在MainActivity中利用SimpleAdapter绑定组件进行for循环遍历输出，使用Toast显示选中的列表项信息

- #### ①部分实验代码：

  ```xml
  <LinearLayout
          android:id="@+id/list_unit_01"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:orientation="horizontal"
          app:layout_constraintBottom_toBottomOf="parent"
          app:layout_constraintEnd_toEndOf="parent"
          app:layout_constraintStart_toStartOf="parent"
          app:layout_constraintTop_toTopOf="parent"
          android:onClick="click_select">
  
          <TextView
              android:id="@+id/list_unit_01_name"
              android:layout_width="0dp"
              android:layout_height="match_parent"
              android:layout_gravity="fill"
              android:layout_weight="1"
              android:layout_marginLeft="10dp"
              android:gravity="center_vertical|start"
              android:textSize="18sp" />
  
  ```

- #### ②部分实验代码：

  ```java
      //click_to_select block
      public void click_select (View V) throws Exception{
          LinearLayout list_unit = V.findViewById(R.id.list_unit_01);
          TextView name = V.findViewById(R.id.list_unit_01_name);
              if (view_select.get(V) == null || !view_select.get(V)) {
                  list_unit.setBackgroundColor(Color.BLUE);
                  view_select.put(V, true);
                  Toast toast = Toast.makeText(MainActivity.this, name.getText(), Toast.LENGTH_SHORT);
                  toast.show();
              } else {
                  list_unit.setBackgroundColor(Color.WHITE);
                  view_select.put(V, false);
                  AlertDialog.Builder builder = new AlertDialog.Builder(this);
                  builder.setView(View.inflate(this, R.layout.alert, null));
                  builder.show();
              }
      }
  ```

- #### 实验结果如下图：

- <img src="https://github.com/lyhah/Android-/blob/main/andr%E6%88%AA%E5%9B%BE/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-11-15%20203425.png" style="zoom:20%;" />

### 2.创建自定义布局的AlertDialog

- #### 思路：

 调用AlertDialog.Builder对象上的setView()将布局添加到AlertDialog
 
- #### 部分实验代码：

  ```xml
  <TableLayout
          android:id="@+id/alert"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          app:layout_constraintStart_toStartOf="parent"
          app:layout_constraintTop_toTopOf="parent">
  
          <TableRow
              android:layout_width="match_parent"
              android:layout_height="match_parent">
  
              <TextView
                  android:id="@+id/alert_title"
                  android:layout_width="match_parent"
                  android:layout_height="80dp"
                  android:layout_weight="1"
                  android:background="#FFE600"
                  android:fontFamily="cursive"
                  android:gravity="center"
                  android:textColor="@color/colorPrimary"
                  android:text="ANDROID APP"
                  android:textSize="24sp" />
          </TableRow>
  
  					…………………………
  ```
  

- #### 实验结果如下图：

- <img src="https://github.com/lyhah/Android-/blob/main/andr%E6%88%AA%E5%9B%BE/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-11-15%20204334.png" alt="avatar" style="zoom:50%; width:750px" />

### 3.使用XML定义菜单

- #### 思路：

  ①创建menu_demo.xml编写菜单样式

  ②在MenuActivity中装填对应的菜单并添加到menu中

- #### 部分实验代码：

  ```xml
  <menu>
      <item android:title="字体大小">
          <menu >
              <item
                  android:id="@+id/font_small"
                  android:title="小" />
              <item
                  android:id="@+id/font_mid"
                  android:title="中" />
              <item
                  android:id="@+id/mi_big"
                  android:title="大" />
          </menu>
      </item>
  </menu>
  ```
  


- #### 实验结果如下图：

- <img src="https://github.com/lyhah/Android-/blob/main/andr%E6%88%AA%E5%9B%BE/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-11-15%20204358.png" alt="avatar" style="zoom:50%; width:750px" />

### 4.创建上下文操作模式的上下文菜单

- #### 思路：

 使用ListView创建List
 
 为List Item创建ActionMode形式的上下文菜单

- #### 部分代码：

  ```java
  public void onCreateContextMenu(ContextMenu menu, View v,
                                  ContextMenuInfo menuInfo) {
      super.onCreateContextMenu(menu, v, menuInfo);
      MenuInflater inflater = getMenuInflater();
      inflater.inflate(R.menu.menu_blank, menu);
  }
  
  ……………………
      
  ActionMode.Callback callback = new ActionMode.Callback()
      {
  
          @Override
          public boolean onCreateActionMode(ActionMode actionMode, Menu menu)
          {
              getMenuInflater().inflate(R.menu.menu_blank, menu);
              return true;
          }
  
          …………
  
          @Override
          public boolean onActionItemClicked(ActionMode actionMode, MenuItem menuItem)
          {
              actionMode.setTitle(selected_items + " selected");
              return true;
          }
      	
      	…………
      	
      };
  ```

- #### 实验结果如下图：

- <img src="https://github.com/lyhah/Android-/blob/main/andr%E6%88%AA%E5%9B%BE/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-11-15%20204439.png" style="zoom:50%; width:750px" />


