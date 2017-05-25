# NotePad
This is an AndroidStudio rebuild of google SDK sample NotePad
# 实现了两个基本功能


## 1.显示note时间戳

### 要实现时间戳的功能要修改映射到数据库的PROJECTTION,ViweID,datacloumn,在LISTITEM中添加时间戳的textview.然后再Noteeditor修改时间戳的格式。


![Image text](https://raw.githubusercontent.com/lyc666666/NOTepad/master/app/src/main/res/123/2.jpg)

####  <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/icon"
            android:layout_weight="5"
            android:src="@drawable/app_notes"/>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:layout_weight="1"
            >
            <TextView xmlns:android="http://schemas.android.com/apk/res/android"
                android:id="@android:id/text1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:textColor="#696969"
                android:textAppearance="?android:attr/textAppearanceLarge"
                android:gravity="center_vertical"
                android:paddingLeft="5dip"
                android:singleLine="true"
                />
            <TextView xmlns:android="http://schemas.android.com/apk/res/android"
                android:id="@android:id/text2"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:textColor="#696969"
                android:textAppearance="?android:attr/textAppearanceLarge"
                android:gravity="center_vertical"
                android:paddingLeft="5dip"
                android:singleLine="true"
                />
## 2.实现note的搜索功能


###  实现搜索功能，创建一个新的Activity，再其layout中加入listview控件。在NoteList的optionmenu添加一条新的Item，创建点击事件通过intent跳到NoteSearch这个新的Activity中，设置searchview的监听事件，重写onQueryTextChange方法。通过title和time完成搜索
#### String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE,NotePad.Notes.COLUMN_NAME_CREATE_DATE  } ;

        
        int[] viewIDs = { android.R.id.text1,android.R.id.text2 };

        
        SimpleCursorAdapter adapter
            = new SimpleCursorAdapter(
                      this,                             // The Context for the ListView
                      R.layout.noteslist_item,          // Points to the XML for a list item
                      cursor,                           // The cursor to get items from
                      dataColumns,
                      viewIDs
              );

       
    }

   
    public boolean onCreateOptionsMenu(Menu menu) {
        
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.list_options_menu, menu);

        
        Intent intent = new Intent(null, getIntent().getData());
        intent.addCategory(Intent.CATEGORY_ALTERNATIVE);
        menu.addIntentOptions(Menu.CATEGORY_ALTERNATIVE, 0, 0,
                new ComponentName(this, NotesList.class), null, intent, 0, null);

        return super.onCreateOptionsMenu(menu);
    }
![Image text](https://raw.githubusercontent.com/lyc666666/NOTepad/master/app/src/main/res/123/1.jpg)

![Image text](https://raw.githubusercontent.com/lyc666666/NOTepad/master/app/src/main/res/123/3.jpg)

