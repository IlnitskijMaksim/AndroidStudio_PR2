# Практична робота №1.2
### Тема роботи:
Створення першої програми в Android Studio для ОС Android.
### Мета роботи:
Отримати досвід роботи із процесамм відстеження станів активності.
# Хід роботи

### Методи onPause, onStart, onRestart
Було методи onPause, onStart, onRestart. Коли цей метод викликається виводиться сповіщення про виклик цього метод

```java
package com.example.pr1;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private Button simpleButton;
    private TextView simpleTextView;
    private int i = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Log.d("MainActivity", "onCreate called"); // Додано логування

        simpleButton = findViewById(R.id.simpleButton);
        simpleTextView = findViewById(R.id.simpleTextView);
        simpleButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (i == 0) {
                    simpleTextView.setText("Hello!");
                    i++;
                }
                else if (i == 1){
                    simpleTextView.setText("Stop pressing me!");
                    i++;
                }
                else {
                    simpleTextView.setText("\uD83D\uDE21\uD83D\uDE21\uD83D\uDE21\uD83D\uDE21\uD83D\uDE21\uD83D\uDE21\uD83D\uDE21");
                    i = 0;
                }
            }
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
        showScreenMessage("App started", Toast.LENGTH_SHORT);
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        showScreenMessage("App restarted", Toast.LENGTH_SHORT);
    }

    @Override
    protected void onPause() {
        super.onPause();
        showScreenMessage("App paused", Toast.LENGTH_SHORT);
    }

    private void showScreenMessage(String message, int duration) {
        Toast.makeText(this, message, duration).show();
    }
}
```

### Як працює програма

https://github.com/IlnitskijMaksim/AndroidStudio_PR2/assets/112692170/0e340262-a4ac-4591-a215-4feb2a8725d7

