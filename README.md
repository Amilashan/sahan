
................Two Value..................


public class MainActivity extends AppCompatActivity {

  EditText editText1,editText2;
  Button button;
  TextView textView;


    @SuppressLint("WrongViewCast")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText1 = (EditText) findViewById(R.id.value1);
        editText2 = (EditText) findViewById(R.id.value2);
        button =(Button) findViewById(R.id.button);
        textView= (TextView)  findViewById(R.id.display);


        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                String data1 = editText1.getText().toString();
                String data2 = editText2.getText().toString();

                Integer number1 = Integer.valueOf(data1);
                Integer number2 = Integer.valueOf(data2);

                Integer Add = number1+number2;

                String AddString = String.valueOf(Add);

                textView.setText(AddString);



            }
        });
    }
}

...................Calculator................


public class MainActivity extends AppCompatActivity {
    EditText editText1,editText2;
    RadioButton add,sub,mul,div;
    Button button;
    TextView textView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText1 = (EditText) findViewById(R.id.value1);
        editText2 = (EditText) findViewById(R.id.value2);
        add = (RadioButton) findViewById(R.id.radioButton1);
        sub = (RadioButton) findViewById(R.id.radioButton2);
        div = (RadioButton) findViewById(R.id.radioButton3);
        mul = (RadioButton) findViewById(R.id.radioButton4);
        button = (Button) findViewById(R.id.button);
        textView = (TextView) findViewById(R.id.display);

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                
            }
        });

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                String data1 = editText1.getText().toString();
                String data2 = editText2.getText().toString();

                if (data1.isEmpty() || data2.isEmpty()){
                    Toast.makeText(MainActivity.this, "Values are Empty Check Again", Toast.LENGTH_SHORT).show();
                }
                else {
                    Integer number1 = Integer.valueOf(data1);
                    Integer number2 = Integer.valueOf(data2);

                    if (add.isChecked()){
                        Integer addOutput = number1+number2;

                        String convertedAdd = String.valueOf(addOutput);
                        textView.setText(convertedAdd);
                    }
                    else if (sub.isChecked()){
                        Integer subOutput = number1-number2;

                        String convertedSub = String.valueOf(subOutput);
                        textView.setText(convertedSub);

                    }
                    else if (mul.isChecked()) {
                        Integer mulOutput = number1*number2;

                        String convertedMul = String.valueOf(mulOutput);
                        textView.setText(convertedMul);
                    }
                    else if (div.isChecked()){
                        Integer divOutput = number1/number2;

                        String convertedDiv = String.valueOf(divOutput);
                        textView.setText(convertedDiv);

                    }
                }



            }
        });

    }
}


..................Data Send.................

Activity.....


public class MainActivity extends AppCompatActivity {

    EditText editText1,editText2,editText3;
    Button button;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText1 = (EditText) findViewById(R.id.id1);
        editText2 = (EditText) findViewById(R.id.id2);
        editText3 = (EditText) findViewById(R.id.id3);
        button = (Button) findViewById(R.id.button);


        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                String data1 = editText1.getText().toString();
                String data2 = editText2.getText().toString();
                String data3 = editText3.getText().toString();

                if (data1.equals("android") && data3.equals("android")){

                    Intent intent = new Intent(MainActivity.this,ProfileActivity.class);

                        intent.putExtra("Username",data1);
                        intent.putExtra("Email",data2);

                        startActivity(intent);

                }
                else{
                    Toast.makeText(MainActivity.this, "Compared Values are not matched", Toast.LENGTH_SHORT).show();
                }
            }
        });


    }
}


..............Profile.........................


public class ProfileActivity extends AppCompatActivity {

    TextView textView1,textView2;



    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_profile);

        textView1 = (TextView) findViewById(R.id.display1);
        textView2 = (TextView) findViewById(R.id.display2);

        Bundle bundle = getIntent().getExtras();

        if (bundle != null){
            String name = bundle.getString("Username");
            textView1.setText(name);

            String email = bundle.getString("Email");
            textView2.setText(email);
        }
    }
}

.........Relative............


<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="10dp"
    tools:context=".MainActivity">

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/top">
    </Button>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/first"
        android:layout_below="@id/top">
    </Button>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/second"
        android:layout_alignParentRight="true"
        android:layout_below="@id/top">
    </Button>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/third"
        android:layout_below="@id/second">
    </Button>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/fourth"
        android:layout_below="@id/second"
        android:layout_alignParentRight="true"
        android:layout_toRightOf="@id/third"
        >
    </Button>



</RelativeLayout>
