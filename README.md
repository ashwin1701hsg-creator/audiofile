# Ex.No:3 Develop a simple application to play and control the audio file in android studio.


## AIM:

To develop a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as audiofile and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml and create start,pause and stop button.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to play and control the audio file”.
Developed by: Ashwin H
Reg Number : 212225230025
*/
```
### MainActivity.java
```java
package com.example.pmdexp_3;

import androidx.appcompat.app.AppCompatActivity;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize buttons as local variables
        Button btnPlay = findViewById(R.id.btnPlay);
        Button btnPause = findViewById(R.id.btnPause);
        Button btnStop = findViewById(R.id.btnStop);

        // Create initial MediaPlayer instance
        initializeMediaPlayer();

        // PLAY Button - Use Lambda
        btnPlay.setOnClickListener(v -> {
            if (mediaPlayer != null && !mediaPlayer.isPlaying()) {
                mediaPlayer.start();
                showToast("Playing audio...");
            }
        });

        // PAUSE Button - Use Lambda
        btnPause.setOnClickListener(v -> {
            if (mediaPlayer != null && mediaPlayer.isPlaying()) {
                mediaPlayer.pause();
                showToast("Audio paused");
            }
        });

        // STOP Button - Use Lambda
        btnStop.setOnClickListener(v -> {
            if (mediaPlayer != null) {
                if (mediaPlayer.isPlaying()) {
                    mediaPlayer.stop();
                }
                // IMPORTANT: Release the old instance before creating a new one
                mediaPlayer.release();
                initializeMediaPlayer();
                showToast("Audio stopped");
            }
        });
    }

    private void initializeMediaPlayer() {
        mediaPlayer = MediaPlayer.create(this, R.raw.audio);
        if (mediaPlayer == null) {
            showToast("Failed to load audio resource");
        }
    }

    private void showToast(String message) {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        // Always release resources when the Activity is destroyed
        if (mediaPlayer != null) {
            mediaPlayer.release();
            mediaPlayer = null;
        }
    }
}
```
### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Simple Audio Player"
        android:textSize="20sp"
        android:layout_marginBottom="30dp"/>

    <Button
        android:id="@+id/btnPlay"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PLAY"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnPause"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="PAUSE"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

    <Button
        android:id="@+id/btnStop"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:text="STOP"
        android:textSize="16sp"
        android:layout_margin="10dp"/>

</LinearLayout>
```

## OUTPUT
### START
<img width="985" height="522" alt="image" src="https://github.com/user-attachments/assets/7dcefa25-fac7-4b91-85e3-664d9a99709b" />


### PAUSE
<img width="962" height="510" alt="image" src="https://github.com/user-attachments/assets/8505c4e8-d8c3-498c-a97e-50b22483d865" />

### STOP
<img width="942" height="517" alt="image" src="https://github.com/user-attachments/assets/a3f83833-387f-4754-9de8-9d74c65e5ae1" />



## RESULT
   Thus a simple application, to play and control the audio file and to perfrom the start,pause and stop opeartion in Android Studio is developed and executed successfully.
