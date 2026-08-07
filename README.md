
# Ex.No:3 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)


## ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as SMSIntent and click Next.

Step 3: Select the Minimum SDK below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally, click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details given in the MainActivity file.

Step 7: Save and run the application.


## Program:
 ```
/*
Program to create and design an android application for Sending  SMS using Intent.
Developed by: TARANIKKA A
RegisterNumber: 212223220115
*/
```

## MainActivity.java:

```
package com.example.sms_app;

import android.Manifest;
import android.content.pm.PackageManager;
import android.os.Bundle;
import android.telephony.SmsManager;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

public class MainActivity extends AppCompatActivity {

    EditText etPhone, etMessage;
    Button btnSend;

    private static final int SMS_PERMISSION_CODE = 101;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etPhone = findViewById(R.id.etPhone);
        etMessage = findViewById(R.id.etMessage);
        btnSend = findViewById(R.id.btnSend);

        // Ask for SMS permission
        if (ContextCompat.checkSelfPermission(this, Manifest.permission.SEND_SMS)
                != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this,
                    new String[]{Manifest.permission.SEND_SMS}, SMS_PERMISSION_CODE);
        }

        btnSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String phone = etPhone.getText().toString().trim();
                String message = etMessage.getText().toString().trim();

                if (phone.isEmpty() || message.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Please enter phone and message", Toast.LENGTH_SHORT).show();
                } else {
                    try {
                        SmsManager smsManager = SmsManager.getDefault();
                        smsManager.sendTextMessage(phone, null, message, null, null);
                        Toast.makeText(MainActivity.this, "SMS Sent!", Toast.LENGTH_SHORT).show();
                    } catch (Exception e) {
                        Toast.makeText(MainActivity.this, "Failed to send SMS", Toast.LENGTH_SHORT).show();
                    }
                }
            }
        });
    }
}
```

## activity_main.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/etPhone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter phone number"
        android:inputType="phone" />

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter message"
        android:inputType="textMultiLine"
        android:lines="4"
        android:gravity="top" />

    <Button
        android:id="@+id/btnSend"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send SMS" />

</LinearLayout>

```

## AndroidMainfest.xml

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />

    <uses-permission android:name="android.permission.SEND_SMS"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.SMS_App">

        <activity
            android:name=".MainActivity"
            android:exported="true"
            tools:ignore="DuplicateActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## OUTPUT:

### activity_main.xml
<img width="1919" height="1084" alt="image" src="https://github.com/user-attachments/assets/e782f6ca-63dd-496c-a297-471a14a56f62" />


### MainActivity.java
<img width="1919" height="1083" alt="image" src="https://github.com/user-attachments/assets/6159beb9-f163-4866-b38f-010a62c38afd" />


### AndroidManifist.xml
<img width="1919" height="1089" alt="image" src="https://github.com/user-attachments/assets/5622bf38-8fdb-46d5-a356-0819f5e62bdb" />


### SmsApp
![WhatsApp Image 2025-10-08 at 09 34 24_c00c4650](https://github.com/user-attachments/assets/f256e5d2-9831-4803-964d-fd557cc71b5f)
![WhatsApp Image 2025-10-08 at 09 34 43_838e8f8d](https://github.com/user-attachments/assets/9d0f9d92-04cf-46e3-96b1-6b91409a3bb3)


## RESULT:
Thus a Simple Android Application to create and design an android application for Sending SMS using Intent in Android Studio was developed and executed successfully.
