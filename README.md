# My-Score-Keaper-App
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/court"
    tools:context="com.example.android.footballkeaper.MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="Football Score Keaper"
        android:textColor="#f4e912"
        android:textSize="30sp" />

    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="80dp"
        android:orientation="horizontal">

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginLeft="5dp"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="FC Barcelona"
                android:textColor="#faea03"
                android:textSize="24sp" />

            <TextView
                android:id="@+id/barca"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center_horizontal"
                android:text="0"
                android:textColor="#ffff"
                android:textSize="60sp" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:onClick="scorebarca"
                android:text="+1 Goal" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center_horizontal"
                android:text="0"
                android:textColor="#ffff"
                android:textSize="60sp"
                android:id="@+id/faulb"/>

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="+1 Faul"
                android:onClick="faulbarca"/>

        </LinearLayout>

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginLeft="10dp"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Real Madrid"
                android:textColor="#fcdf03"
                android:textSize="25sp" />

            <TextView
                android:id="@+id/real"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center_horizontal"
                android:text="0"
                android:textColor="#ffff"
                android:textSize="60sp" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:onClick="scorereal"
                android:text="+1 Goal" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center_horizontal"
                android:text="0"
                android:textColor="#ffff"
                android:textSize="60sp"
                android:id="@+id/faulr"/>

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="+1 Faul"
                android:onClick="faulreal"/>

        </LinearLayout>

    </LinearLayout>

    <Button
        android:id="@+id/reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/linearLayout"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp"
        android:text="Reset"
        android:onClick="reset"/>

    <Button
        android:id="@+id/winner"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:text="Winner Team"
        android:onClick="winner"/>

    <TextView
        android:id="@+id/win"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentRight="true"
        android:textColor="#f1e90b"
        android:textSize="50sp"
        />

</RelativeLayout>
...............................................................................................................


public class MainActivity extends AppCompatActivity {
    int scorebarcelona =0;
    int scorereal=0;
    int faulbarcelona=0;
    int faulreal=0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    public void displayForBarca(int score) {
        TextView scoreView = (TextView) findViewById(R.id.barca);
        scoreView.setText(String.valueOf(score));
    }
    public void displayForReal(int score) {
        TextView scoreView = (TextView) findViewById(R.id.real);
        scoreView.setText(String.valueOf(score));
    }

    public void scorebarca(View View)
    {
        scorebarcelona=scorebarcelona+1;
        displayForBarca(scorebarcelona);
    }
    public void scorereal(View View)
    {
        scorereal=scorereal+1;
        displayForReal(scorereal);
    }
    ///////////////////////////////////////////////////
    public void displayForbarca(int score) {
        TextView scoreView = (TextView) findViewById(R.id.faulb);
        scoreView.setText(String.valueOf(score));
    }

    public void faulbarca(View v)
    {
        faulbarcelona=faulbarcelona+1;
        displayForbarca(faulbarcelona);
    }

    public void displayForreal(int score) {
        TextView scoreView = (TextView) findViewById(R.id.faulr);
        scoreView.setText(String.valueOf(score));
    }
    public void faulreal(View v)
    {
        faulreal=faulreal+1;
        displayForreal(faulreal);
    }
    public void reset(View v)
    {
        faulreal=0;
        faulbarcelona=0;
        scorereal=0;
        scorebarcelona=0;
        displayForreal(0);
        displayForbarca(0);
        displayForBarca(0);
        displayForReal(0);
    }
    public void winner(View v)
    {
        if(scorebarcelona>scorereal)
        {
            TextView scoreView = (TextView) findViewById(R.id.win);
            scoreView.setText(String.valueOf("Barcelona"));
        }
        else if(scorereal>scorebarcelona)
        {
            TextView scoreView = (TextView) findViewById(R.id.win);
            scoreView.setText(String.valueOf("Real Madrid"));
        }
        else
        {
            TextView scoreView = (TextView) findViewById(R.id.win);
            scoreView.setText(String.valueOf("no winner"));
        }
    }
}
