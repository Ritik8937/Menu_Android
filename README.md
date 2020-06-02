# Menu_Android

Here we will learn different types of menus like Optionmenu , context and Pop Menu  

Let discuss each of them one by one.

# 1.Option Menu 

Here we will be take 3 files Main Activity and Menu main xml file where we will take items list.

# Main Activity Java file 

    package com.example.application;

    import androidx.appcompat.app.AppCompatActivity;
    import androidx.appcompat.widget.Toolbar;
    import android.os.Bundle;
    import android.view.Menu;
    import android.view.MenuItem;
    import android.view.View;
    import android.widget.EditText;
    import android.widget.Toast;




    public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu)
    {   getMenuInflater().inflate(R.menu.menu_main,menu);
        return true;
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item)
    {
        int id = item.getItemId();
        if (id == R.id.profile)
        {
            Toast.makeText(getApplicationContext(), "Profile", Toast.LENGTH_LONG).show();
            return true;
        }
        if ((id == R.id.setting))
        {

            Toast.makeText(getApplicationContext(), "Setting", Toast.LENGTH_LONG).show();
            return true;
        }
        return true;
    }

}

# Main Activity xml

    <?xml version="1.0" encoding="utf-8"?>
    <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/customLayout"
    android:layout_width="match_parent"

    android:layout_height="match_parent"
    tools:context="com.example.application.MainActivity"/>
    
 # Menu_main xml
 
 
 
 
    <?xml version="1.0" encoding="utf-8"?>
    <menu xmlns:tools="http://schemas.android.com/tools"
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto">

        <item
            android:orderInCategory="100"
            android:id="@+id/profile"
            android:title="Profile"
            android:showAsAction="never"
            tools:ignore="AppCompatResource">

        </item>
        <item
            android:orderInCategory="101"
            android:id="@+id/setting"
            android:title="Setting">

        </item>

</menu>
 
# 2.Context Menu 

Here we will be take 3 files Main Activity and Menu main xml file where we will take items list.

# Main Activity Java file 

package com.example.application;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import android.os.Bundle;
import android.view.ContextMenu;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;




public class MainActivity extends AppCompatActivity {
    Button b;
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        b=(Button)findViewById(R.id.button);
        registerForContextMenu(b);
    }
    @Override
    public void onCreateContextMenu(ContextMenu menu,View view,ContextMenu.ContextMenuInfo contextmenuinfo)
    {
        getMenuInflater().inflate(R.menu.menu_main,menu);
        super.onCreateContextMenu(menu,view,contextmenuinfo);
    }
    @Override
    public boolean onContextItemSelected(MenuItem menu)
    {
        int id = menu.getItemId();
        if (id == R.id.profile)
        {
            Toast.makeText(getApplicationContext(), "Profile", Toast.LENGTH_LONG).show();
            return true;
        }
        if ((id == R.id.setting))
        {

            Toast.makeText(getApplicationContext(), "Setting", Toast.LENGTH_LONG).show();
            return true;
        }
        return true;
    }
    }
   
# Main Activity xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/customLayout"
    android:layout_width="match_parent"

    android:layout_height="match_parent"
    tools:context="com.example.application.MainActivity">

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Dynamic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>


 # Menu_main xml
 
 <?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto">

        <item
            android:orderInCategory="100"
            android:id="@+id/profile"
            android:title="Profile"
            android:showAsAction="never"
            tools:ignore="AppCompatResource">

        </item>
        <item
            android:orderInCategory="101"
            android:id="@+id/setting"
            android:title="Setting">

        </item>

</menu>

# 3.PopUp Menu 

Here we will be take 3 files Main Activity and Menu main xml file where we will take items list.

# Main Activity Java file 

    package com.example.application;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import android.os.Bundle;
import android.view.ContextMenu;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.PopupMenu;
import android.widget.Toast;




public class MainActivity extends AppCompatActivity {
    Button b;
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        b=(Button)findViewById(R.id.button);
        /*b.setOnClickListener(new View.OnClickListener() {
                                 @Override
                                 public void onClick(View v)
                                 {
                                     final PopupMenu popupMenu= new PopupMenu(MainActivity.this,b);
                                     getMenuInflater().inflate(R.menu.menu_main,popupMenu.getMenu());
                                     popupMenu.setOnMenuItemClickListener(new PopupMenu.OnMenuItemClickListener() {
                                         @Override
                                         public boolean onMenuItemClick(MenuItem item) {
                                             int id = item.getItemId();
                                             if (id == R.id.profile)
                                             {
                                                 Toast.makeText(getApplicationContext(), "Profile", Toast.LENGTH_LONG).show();
                                                 return true;
                                             }
                                             if ((id == R.id.setting))
                                             {

                                                 Toast.makeText(getApplicationContext(), "Setting", Toast.LENGTH_LONG).show();
                                                 return true;
                                             }
                                             popupMenu.dismiss();
                                             return true;
                                         }
                                     });
                                     popupMenu.show();
                                 }
                             });*/
    registerForContextMenu(b);
    }
    @Override
    public void onCreateContextMenu(ContextMenu menu,View view,ContextMenu.ContextMenuInfo contextmenuinfo)
    {
        getMenuInflater().inflate(R.menu.menu_main,menu);
        super.onCreateContextMenu(menu,view,contextmenuinfo);
    }
    @Override
    public boolean onContextItemSelected(MenuItem menu)
    {
        int id = menu.getItemId();
        if (id == R.id.profile)
        {
            Toast.makeText(getApplicationContext(), "Profile", Toast.LENGTH_LONG).show();
            return true;
        }
        if ((id == R.id.setting))
        {

            Toast.makeText(getApplicationContext(), "Setting", Toast.LENGTH_LONG).show();
            return true;
        }
        return true;
    }


}
# Main Activity xml

    <?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/customLayout"
    android:layout_width="match_parent"

    android:layout_height="match_parent"
    tools:context="com.example.application.MainActivity">

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Dynamic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>




    
 # Menu_main xml
 
 <?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto">

        <item
            android:orderInCategory="100"
            android:id="@+id/profile"
            android:title="Profile"
            android:showAsAction="never"
            tools:ignore="AppCompatResource"
            android:icon="@drawable/ic_attachment_black_24dp">

        </item>
        <item
            android:orderInCategory="101"
            android:id="@+id/setting"
            android:title="Setting">

        </item>

</menu>
