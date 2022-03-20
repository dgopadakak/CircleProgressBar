# CircleProgressBar
Circle progress bar on Java for Android Studio<br>
<br>
Put this into your MAinActivity.java:
```java
import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.ProgressBar;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity
{
    private int progress = 0;

    private ProgressBar progressBar;
    private TextView textViewProgress;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        progressBar = findViewById(R.id.progress_bar);
        textViewProgress = findViewById(R.id.text_view_progress);

        progressBar.setProgress(0);
        textViewProgress.setText("0%");
    }

    public void onClickUp(View view)
    {
        if (progress <= 90)
        {
            progress += 10;
            updateProgressBar();
        }
    }

    public void onClickLow(View view)
    {
        if (progress >= 10)
        {
            progress -= 10;
            updateProgressBar();
        }
    }

    private void updateProgressBar()
    {
        progressBar.setProgress(progress);
        textViewProgress.setText(progress + "%");
    }
}
```
<br>
Then, put this into your activity_main.xml:<br>

```xml
<ProgressBar
    android:id="@+id/progress_bar"
    style="@style/CircularDeterminateProgressBar"
    android:layout_width="200dp"
    android:layout_height="200dp"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintLeft_toLeftOf="parent"
    app:layout_constraintRight_toRightOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    tools:progress="0" />

<TextView
    android:id="@+id/text_view_progress"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textAppearance="@style/TextAppearance.AppCompat.Large"
    app:layout_constraintBottom_toBottomOf="@+id/progress_bar"
    app:layout_constraintEnd_toEndOf="@+id/progress_bar"
    app:layout_constraintStart_toStartOf="@+id/progress_bar"
    app:layout_constraintTop_toTopOf="@+id/progress_bar"
    tools:text="0%" />

<Button
    android:id="@+id/button_decr"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:onClick="onClickLow"
    android:text="- 10%"
    app:layout_constraintStart_toStartOf="@+id/progress_bar"
    app:layout_constraintTop_toBottomOf="@+id/progress_bar" />

<Button
    android:id="@+id/button_incr"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:onClick="onClickUp"
    android:text="+ 10%"
    app:layout_constraintEnd_toEndOf="@+id/progress_bar"
    app:layout_constraintTop_toBottomOf="@+id/progress_bar" />
```
