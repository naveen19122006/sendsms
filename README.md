
# Ex.No:3 Design an android application Send SMS using Intent.

## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application Send SMS using Intent.
Developed by: Naveen Kumar E
Registeration Number : 212224230181
*/
```
### MainActivity.java
```java
package com.example.exp3;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private EditText etPhoneNumber;
    private EditText etMessage;
    private Button btnSendSms;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        etPhoneNumber = findViewById(R.id.etPhoneNumber);
        etMessage = findViewById(R.id.etMessage);
        btnSendSms = findViewById(R.id.btnSendSms);

        btnSendSms.setOnClickListener(v -> {
            String phoneNumber = etPhoneNumber.getText().toString().trim();
            String message = etMessage.getText().toString().trim();

            if (phoneNumber.isEmpty()) {
                Toast.makeText(MainActivity.this, "Please enter a phone number", Toast.LENGTH_SHORT).show();
            } else {
                Intent intent = new Intent(Intent.ACTION_SENDTO);
                intent.setData(Uri.parse("smsto:" + phoneNumber));
                intent.putExtra("sms_body", message);

                try {
                    startActivity(intent);
                } catch (ActivityNotFoundException e) {
                    Toast.makeText(MainActivity.this, "No SMS app found", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }
}

```
### Activitymain.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp"
    android:background="#E3F2FD"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send SMS using Intent"
        android:textSize="24sp"
        android:textStyle="bold"
        android:textColor="#0D47A1"
        android:layout_marginBottom="32dp" />

    <EditText
        android:id="@+id/etPhoneNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter phone number"
        android:inputType="phone"
        android:padding="14dp"
        android:background="@android:color/white"
        android:textColor="#212121"
        android:textColorHint="#757575"
        android:layout_marginBottom="16dp" />

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your message"
        android:inputType="textMultiLine"
        android:minLines="3"
        android:gravity="top|start"
        android:padding="14dp"
        android:background="@android:color/white"
        android:textColor="#212121"
        android:textColorHint="#757575"
        android:layout_marginBottom="24dp" />

    <Button
        android:id="@+id/btnSendSms"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        android:backgroundTint="#1976D2"
        android:textColor="@android:color/white" />

</LinearLayout>

```
## OUTPUT
<img width="1920" height="1160" alt="image" src="https://github.com/user-attachments/assets/438b102f-521f-4488-80f0-96672ae6499a" />
<img width="1920" height="1160" alt="image" src="https://github.com/user-attachments/assets/25eb3fc0-df27-4076-8a0b-8f753053b56a" />


## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
