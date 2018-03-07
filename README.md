MainActivity.java
package net.onest.a01helloandroid;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.ViewGroup;
import android.widget.DatePicker;
import android.widget.LinearLayout;
import android.widget.TextView;
import android.widget.TimePicker;
import android.widget.Toast;

import java.text.SimpleDateFormat;
import java.util.Calendar;

public class MainActivity extends AppCompatActivity {
    private TextView thrd;
    private DatePicker datePicker;
    private TimePicker timePicker;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        datePicker = findViewById(R.id.datePicker);
        timePicker = findViewById(R.id.timePicker);
        datePicker.init(2018, 2, 6, new DatePicker.OnDateChangedListener() {
            @Override
            public void onDateChanged(DatePicker view, int year,
                                      int monthOfYear, int dayOfMonth) {
                // 获取一个日历对象，并初始化为当前选中的时间
                Calendar calendar = Calendar.getInstance();
                calendar.set(year, monthOfYear, dayOfMonth);
                SimpleDateFormat format = new SimpleDateFormat(
                        "yyyy年MM月dd日  HH:mm");
                Toast.makeText(getApplicationContext(),
                        format.format(calendar.getTime()), Toast.LENGTH_SHORT)
                        .show();
            }
        });

        timePicker.setIs24HourView(true);
        timePicker
                .setOnTimeChangedListener(new TimePicker.OnTimeChangedListener() {
                    @Override
                    public void onTimeChanged(TimePicker view, int hourOfDay,
                                              int minute) {
                        Toast.makeText(getApplicationContext(),
                                hourOfDay + "小时" + minute + "分钟",
                                Toast.LENGTH_SHORT).show();
                    }
                });


    }

    private void codeLayout() {
        LinearLayout.LayoutParams tvParams = new LinearLayout.LayoutParams(LinearLayout.LayoutParams.MATCH_PARENT, LinearLayout.LayoutParams.WRAP_CONTENT);
        TextView textView = new TextView(this);
        textView.setText("新增");
        textView.setLayoutParams(tvParams);
        setContentView(textView);
    }

}



activity_main.xml
<?xml version="1.0" encoding="utf-8"?>

<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="net.onest.a01helloandroid.MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/hello" />

        <!--单选按钮-->
        <RadioGroup
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center">

            <RadioButton
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:background="#00ff00"
                android:checked="true"
                android:text="男" />

            <RadioButton
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="女" />
        </RadioGroup>

        <ToggleButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textOff="关"
            android:textOn="开" />

        <DatePicker
            android:id="@+id/datePicker"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" />

        <TimePicker
            android:id="@+id/timePicker"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" />


    </LinearLayout>
</ScrollView>


