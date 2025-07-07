Procedure:
1.	Open Android Studio and create a New Project named EmailApp.
2.	Choose Empty Views Activity and name the main activity as MainActivity.
3.	Open activity_main.xml and design the layout using EditText for username and password, and a Button for login.
4.	In MainActivity.java, write code to handle button click and validate user input.
5.	Run the app on an emulator or physical device.
6.	Enter various combinations of usernames and passwords to check the validation logic.
   
Source Code:

MainActivity.java package com.example.emailapp;
import android.os.Bundle; import android.view.View; import android.widget.Button; import android.widget.EditText; import android.widget.Toast;
import androidx.activity.EdgeToEdge; import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets; import androidx.core.view.ViewCompat; import androidx.core.view.WindowInsetsCompat; public class MainActivity extends AppCompatActivity {
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState); EdgeToEdge.enable(this);
setContentView(R.layout.activity_main);
ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars()); v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom); return insets;
});
EditText et1 = findViewById(R.id.usr);
EditText et2 = findViewById(R.id.pwd); Button buttonLogin = findViewById(R.id.btn);
buttonLogin.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
String username = et1.getText().toString().trim(); String password = et2.getText().toString().trim();
if (username.isEmpty() || password.isEmpty()) {
Toast.makeText(MainActivity.this, "Username or Password is empty",
Toast.LENGTH_SHORT).show();
} else if (username.equals("admin") && password.equals("welcome")) {
Toast.makeText(MainActivity.this, "Login Successful",
Toast.LENGTH_SHORT).show();
} else {
Toast.makeText(MainActivity.this, "Incorrect username or password",
Toast.LENGTH_SHORT).show();
}
}
});
}
}

activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android" android:id="@+id/main" android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:padding="24dp" android:gravity="center" android:background="#EFEFEF">
<EditText android:id="@+id/usr" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Enter Username" android:inputType="textPersonName" />
<EditText android:id="@+id/pwd" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Enter Password" android:inputType="textPassword" android:layout_marginTop="12dp" />
<Button android:id="@+id/btn" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Login" android:layout_marginTop="18dp"
android:backgroundTint="@android:color/holo_blue_dark" android:textColor="#FFFFFF"/>
</LinearLayout>


Output:
Input: Empty username/password → Output: “Username or Password is empty”
Input: admin / welcome → Output: “Login Successful”
Input: any other values → Output: “Incorrect username or password”
