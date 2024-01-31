# CircleProgressBar
Circle progress bar on Java for Android Studio.<br>
<br>
Put this into your MainActivity.java:
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
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

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

</androidx.constraintlayout.widget.ConstraintLayout>
```

<br>
Then create "Drawable Resource File" (this is an .xml file) in res/drawable with the following settings:
<img src="https://github.com/dgopadakak/imagesForOtherMyRepositories/blob/master/CircleProgressBarSettings.jpg" alt="Settings"/>
Put this code into new file "circle":

```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <shape
            android:shape="ring"
            android:thicknessRatio="16"
            android:useLevel="false">
            <solid android:color="#DDD" />
        </shape>
    </item>
    <item>
        <rotate
            android:fromDegrees="270"
            android:toDegrees="270">
            <shape
                android:shape="ring"
                android:thicknessRatio="16"
                android:useLevel="true">
                <gradient
                    android:endColor="#76CD7B"
                    android:centerColor="#53DDD2"
                    android:startColor="#6B33EA"
                    android:type="sweep" />
            </shape>
        </rotate>
    </item>
</layer-list>
```

<br>
You can change colors by using startColor, centerColor and endColor settings.<br>
<br>
Now, if you don't have style.xml file in res/values - just create it with the standard settings and put this code into it:

```xml
<resources>
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/design_default_color_primary</item>
        <item name="colorPrimaryDark">@color/design_default_color_primary_dark</item>
        <item name="colorAccent">#7E5297</item>
    </style>

    <style name="CircularDeterminateProgressBar">
        <item name="android:indeterminateOnly">false</item>
        <item name="android:progressDrawable">@drawable/circle</item>
    </style>

</resources>
```

<br>
<dl>
    <h3>Done!</h3>
</dl>

Thanks for [Coding in Flow](https://gist.github.com/codinginflow) for your [project](https://gist.github.com/codinginflow/477606b85ed11c537a81e80224361878)!
