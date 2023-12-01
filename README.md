<table>
  <tr>
    <th colspan="2">DATA MAHASISWA</th>
  </tr>
  <tr>
    <td>Nama</td>
    <td>Roswanda Nuraini</td>
  </tr>
  <tr>
    <td>NIM</td>
    <td>312210328</td>
  </tr>
  <tr>
    <td>Kelas</td>
    <td>TI.22.A3</td>
  </tr>
  <tr>
    <td>Mata Kuliah</td>
    <td>Pemrograman Mobile</td>
  </tr>
</table>

# Instruksi Tugas

Buatlah tampilan menu Versi 02 dari project-project yang sudah dibuat sebelumnya dengan tambahan memanggil method Maps dengan tampilan sebagai berikut:

![ppppp](https://github.com/roswanda11/Implicit-Intent-V0.2/assets/115516632/1fa474ee-f3a3-415b-8148-4cc06a67373b)

### androidmanifest.xml

    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    
    <uses-permission android:name="android.permission.VIBRATE" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@drawable/downloaded"
        android:label="@string/app_name"
        android:roundIcon="@drawable/downloaded"
        android:supportsRtl="true"
        android:theme="@style/Theme.HelloWorld"
        tools:targetApi="31">
    
        <activity
            android:name="com.helloworld.SplashScreen"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
    
                <action android:name="android.intent.action.VIEW"/>
                <data android:scheme="geo"/>
                <category android:name="android.intent.category.DEFAULT"/>
            </intent-filter>
        </activity>
    
        <activity android:name="com.helloworld.ActivityHomepage" />
        <activity android:name="com.helloworld.MainActivity" />
        <activity android:name="com.helloworld.CountActivity" />
        <activity android:name="com.helloworld.ScrollingActivity" />
        <activity android:name="com.helloworld.FirstActivity" />
        <activity android:name="com.helloworld.SecondActivity" />
        <activity android:name="com.helloworld.AlarmActivity" />
    
        <receiver android:name="com.helloworld.AlarmReceiver" />
    </application>
    </manifest>


### activity_homepage.xml

    <GridLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:columnCount="3"
        android:rowCount="2"
        android:alignmentMode="alignBounds"
        android:useDefaultMargins="true" >
    
        <ImageView
            android:id="@+id/btnHello"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginStart="10dp"
            android:layout_marginEnd="15dp"
            android:src="@drawable/hello" />
    
        <ImageView
            android:id="@+id/btnCount"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginEnd="15dp"
            android:src="@drawable/count" />
    
        <ImageView
            android:id="@+id/btnScrollice"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginEnd="10dp"
            android:src="@drawable/scrollice" />
    
        <ImageView
            android:id="@+id/btnTwoActivity"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginEnd="10dp"
            android:src="@drawable/twoactivity" />
    
        <ImageView
            android:id="@+id/btnAlarm"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginEnd="10dp"
            android:src="@drawable/alarm" />
    
        <ImageView
            android:id="@+id/btnMaps"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginEnd="10dp"
            android:src="@drawable/maps" />
    </GridLayout>

### ActivityHomepage.java

    package com.helloworld;
    
    import android.content.Intent;
    import android.net.Uri;
    import android.os.Bundle;
    import android.view.View;
    import android.widget.ImageView;
    
    import androidx.appcompat.app.AppCompatActivity;
    
    import com.helloworld.R;
    
    public class ActivityHomepage extends AppCompatActivity {
        ImageView btnHello;
        ImageView btnCount;
        ImageView btnScrollice;
        ImageView btnTwoActivity;
        ImageView btnAlarm;
        ImageView btnMaps;
    
    
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_homepage);
    
            btnHello = (ImageView) findViewById(R.id.btnHello);
            btnCount = (ImageView) findViewById(R.id.btnCount);
            btnScrollice = (ImageView) findViewById(R.id.btnScrollice);
            btnTwoActivity = (ImageView) findViewById(R.id.btnTwoActivity);
            btnAlarm = (ImageView) findViewById(R.id.btnAlarm);
            btnMaps = (ImageView) findViewById(R.id.btnMaps);
    
            clickListener();
        }
    
        public void clickListener() {
            btnHello.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Intent helloIntent = new Intent(ActivityHomepage.this, MainActivity.class);
                    startActivity(helloIntent);
                }
            });
    
            btnCount.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Intent countIntent = new Intent(ActivityHomepage.this, CountActivity.class);
                    startActivity(countIntent);
                }
            });
    
            btnScrollice.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Intent scrolliceIntent = new Intent(ActivityHomepage.this, ScrollingActivity.class);
                    startActivity(scrolliceIntent);
                }
            });
    
            btnTwoActivity.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Intent twoIntent = new Intent(ActivityHomepage.this, FirstActivity.class);
                    startActivity(twoIntent);
                }
            });
    
            btnAlarm.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Intent AlarmIntent = new Intent(ActivityHomepage.this, AlarmActivity.class);
                    startActivity(AlarmIntent);
                }
            });
    
            btnMaps.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    Uri gmm = Uri.parse("google.streetview:cbll=46.414382,10.013988");
                    Intent mapIntent = new Intent(Intent.ACTION_VIEW, gmm);
                    mapIntent.setPackage("com.google.android.apps.maps");
                    if (mapIntent.resolveActivity(getPackageManager()) != null) {
                        startActivity(mapIntent);
                    }
                }
            });
        }
    }





