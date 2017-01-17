# psbuiyrfirstandroiddbappsqlite
##3. The User Interface
###1 Building the User Interface for the Todos App
some great websites
- [palette](http://materialpalette.com)
- [icons](http://materialdesignicons.com)
res values colors.xml
```
<resources>
<color name="colorIcons"></color>
</resources>
```

select a new icon name playlist-play, copy vector code
```
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    android:height="24dp"
    android:width="24dp"
    android:viewportWidth="24"
    android:viewportHeight="24">
    <path android:fillColor="#000" android:pathData="M19,9H2V11H19V9M19,5H2V7H19V5M2,15H15V13H2V15M17,13V19L22,16L17,13Z" />
</vector>
```
then in res drawable,create a file called playlist_play.xml


####06:20
strings.xml
```
<resources>
<string name="app_name"</string>
<string-array name="categories_array">
  <item>Home</item>
  <item>Work</item>
</string-array>
</resources>
```

####08:04
```
final ListView lv = (ListView)findViewById(R.id.lvTools);
lv.setAdapter(new ArrayAdapter<String>(this,R.layout.todo_list_item,R.id.tvNode.itemname));
lv.setOnItemClickListener(new AdapterView.OnItemClickListener(){});
```

TodoActivity.java
```
Intent intetn = getIntent();
String content = intent.getStringExtra("Content");
EditText editTOdo = (EditText)findViewById(R.id.editTodo);
eeditTodo.setText(content);
```

##4. Modeling Your Data Schema with Classes
###1 SQLite and Android
```
insert() update() delete() query()
execSQL() rawQuery()
```

###2. The Contract
[BaseColumns](https://developer.android.com/reference/android/provider/BaseColumns.html)
```
public static final class TodosEntry implements BaseColumns{
}
```

###3 The SQLiteOpenHelper Class
```
import android.database.sqlite.SQLiteOpenHelper;
public class DatabaseHelper extends SQLiteOpenHelper{
}
```
