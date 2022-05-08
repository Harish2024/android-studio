## AIM:
To Show Image file sending data from one activity to another activity and Display the output for arithmetic operations using android studio.

## EQUIPMENTS REQUIRED: 
Android Studio(Min. required Artic Fox)

## ALGORITHM: 
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “workshop 2″ and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

stpe 6: Insert the image in drawable file

Step 7: Then select another empty activty.

Step 8: open google page using Implicit Intents and display factorial number using Explicit Intents in MainActivity file.

Step 9: Save and run the application.

## PROGRAM:
```java

### activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <Button
        android:id="@+id/send"
        android:layout_width="254dp"
        android:layout_height="36dp"
        android:text="send image to another activity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.579" />

    <ImageView
        android:id="@+id/img"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintBottom_toTopOf="@+id/send"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/th" />


</androidx.constraintlayout.widget.ConstraintLayout>



### MainActivity.java

package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button Send = (Button) findViewById(R.id.send);

        Send.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // add the image in putExtra
                // and send the data in next activity
                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                String name;
                intent.putExtra( name="myimage", R.drawable.th);
                startActivity(intent);
            }
        });
    }
}




###activity_main2.xml


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <ImageView
        android:id="@+id/img_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="This is my second acitvity"
        android:textColor="#000000"
        tools:layout_editor_absoluteX="125dp"
        tools:layout_editor_absoluteY="192dp" />


</androidx.constraintlayout.widget.ConstraintLayout>



### MainActivity2.java


package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.ImageView;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        ImageView ImageView = (ImageView) findViewById(R.id.img_second);

        // check if any value sent from previous activity
        Bundle bundle = getIntent().getExtras();

        // if bundle is not null then get the image value
        if (bundle != null) {
            int res_image = bundle.getInt("myimage");
            ImageView.setImageResource(res_image);
        }

    }
}

```
### output
![s1](https://user-images.githubusercontent.com/75235789/165439012-79864fe1-d8bb-4ead-9bee-319d36644c61.jpg)
![s2](https://user-images.githubusercontent.com/75235789/165439033-844c88ea-e40d-436e-be83-8608026a9942.jpg)

## Arithmatic Operations
```java




## activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <EditText
        android:id="@+id/editText2"
        android:layout_width="163dp"
        android:layout_height="39dp"
        android:layout_marginBottom="40dp"
        android:hint="Enter number 2"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/buttonsum"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.508"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/editText1"
        android:layout_width="163dp"
        android:layout_height="39dp"
        android:layout_marginBottom="100dp"
        android:hint="Enter  number 1"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/buttonsum"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.508"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/buttonsum"
        android:layout_width="170dp"
        android:layout_height="59dp"
        android:text="Addition"
        app:layout_constraintBottom_toTopOf="@+id/buttonmul"
        app:layout_constraintEnd_toStartOf="@+id/buttonsub"
        app:layout_constraintHorizontal_bias="0.56"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.918" />

    <Button
        android:id="@+id/buttonsub"
        android:layout_width="155dp"
        android:layout_height="57dp"
        android:layout_marginEnd="32dp"
        android:text="Subtraction"
        app:layout_constraintBottom_toTopOf="@+id/buttondiv"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.909" />

    <Button
        android:id="@+id/buttondiv"
        android:layout_width="150dp"
        android:layout_height="57dp"
        android:layout_marginEnd="36dp"
        android:layout_marginBottom="308dp"
        android:text="Division"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <Button
        android:id="@+id/buttonmul"
        android:layout_width="166dp"
        android:layout_height="58dp"
        android:layout_marginBottom="308dp"
        android:text="multiplication"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/buttondiv"
        app:layout_constraintHorizontal_bias="0.54"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/textView1"
        android:layout_width="166dp"
        android:layout_height="71dp"
        android:textAppearance="?android:attr/textAppearanceLarge"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.609"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText2"
        app:layout_constraintVertical_bias="0.452" />

</androidx.constraintlayout.widget.ConstraintLayout>




## MainActivity.java


package com.example.arithmatic;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button btnsum = (Button) findViewById(R.id.buttonsum);
        Button btnsub = (Button) findViewById(R.id.buttonsub);
        Button btndiv = (Button) findViewById(R.id.buttondiv);
        Button btnmul = (Button) findViewById(R.id.buttonmul);
        final EditText etv = (EditText) findViewById(R.id.editText1);
        final EditText etv2 = (EditText) findViewById(R.id.editText2);
        final TextView result = (TextView) findViewById(R.id.textView1);

        btnsum.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                int x = new Integer(etv.getText().toString());
                int y = new Integer(etv2.getText().toString());
                int sum = x + y;
                result.setText( x + " + " + y + " = " + sum);
            }
        });

        btnsub.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                int x = new Integer(etv.getText().toString());
                int y = new Integer(etv2.getText().toString());
                int sub = x - y;
                result.setText( x + " - " + y + " = " + sub);
            }
        });

        btndiv.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                int x = new Integer(etv.getText().toString());
                int y = new Integer(etv2.getText().toString());
                double div = x / y;
                result.setText(x + " / " + y + " = " + div);
            }
        });

        btnmul.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                int x = new Integer(etv.getText().toString());
                int y = new Integer(etv2.getText().toString());
                int mul = x * y;
                result.setText(x + " * " + y + " = " + mul);
            }
        });



    }
}




```
### output
![k4](https://user-images.githubusercontent.com/75235789/165537463-86755004-c369-428b-98f6-ef1f1a71450b.jpg)


![k5](https://user-images.githubusercontent.com/75235789/165537460-07888fbc-e723-491e-adf8-0ab7a9e5a666.jpg)
![k6](https://user-images.githubusercontent.com/75235789/165537450-91c093a5-8f01-4075-b0dd-81ad080d01f2.jpg)

![k7](https://user-images.githubusercontent.com/75235789/165537468-106f7c8b-9c21-421f-b028-b26f3223e1f5.jpg)
![k8](https://user-images.githubusercontent.com/75235789/165537464-7b469340-ff2c-461a-9e9e-d6c48f4af40f.jpg)




### result
Thus a Simple Android Application Show Image file sending data from one activity to another activity and Display the output for arithmetic operations is developed and executed successfully.

