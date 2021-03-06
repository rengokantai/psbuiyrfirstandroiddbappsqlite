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

###4 Creating the Database
in  
TodoListActivity.java
```
protected void onCreate(Bundle savedInstanceState){
    DatavaseHelper helper = new DatabaseHelper(this);
    SQLiteDatabase db = helper.getReadableDatabase();
}
```
cmd
```
sqlite3 app.db
```
some commands
```
.tables
PRAGMA TABLE_INFO(categories);
```
###5 Inserting Records
```
ContentValues values = new ContentValues();
values.pput(TodoEntry.COLUMN_TEXT,"call");
long todo_id = db.insert(TodoENtry.TABLE_NAME,null,values);
```


###6 Reading and Writing
```
String[] projection = {"text","created"}
String selection = "category=?";
String[] selectionArgs = {"1"};
Cursor c = db.query("todos","projection,selection,selectionArgs,null,null,null);
```
is same as
```
select text, created from todos where category=1;
```
##6. Interacting with Data Asynchronously
###1 Asynchronous Data Handling in Android
####03:15
onCreate
```
getLoaderManager().initLoader()
```

onCreateLoader()  
return a CursorLoader object  

onLoadFinished(), onLoadReset
- swapCursor()  

###2 Using the CursorAdapter
```
Cursor c = getContentResolver().query(TodosEntry.CONTENT_URI);
```
then
```
final ListView lv = (ListView)findViewById(R.id.lvTodos);
lv.setAdapter(new ArrayAdapter<String>(this,R.layout.todo_list
```

TodosCursorAdapter.java
```
int textColumn = cursor.getColumnIndex(TodosContract.TodosEntry.COLUMN_TEXT);
String text = cursor.getString(textColumn);
```

