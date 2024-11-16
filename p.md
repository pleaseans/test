01-bmi

MainActivity.kt

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity


class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


        var number1box: EditText = findViewById(R.id.number1box)
        var number2box: EditText = findViewById(R.id.number2box)
        var calbtn: Button = findViewById(R.id.calbtn)
        var result: TextView = findViewById(R.id.outputbox)
        var res:TextView=findViewById(R.id.conc)



//Event Handling Code
        calbtn.setOnClickListener {
            var ht: Float = number1box.text.toString().toFloat()/100
            var wt: Float = number2box.text.toString().toFloat()
            var bmi: Float = wt / (ht * ht)
            result.text = "Result: %.2f".format(bmi)
            when {
                bmi < 18 -> {
                    res.text = "BODY TYPE:Underweight"
                }
                bmi >= 18 && bmi < 25 -> {
                    res.text = "BODY TYPE:Normal"
                }
                bmi >= 25 && bmi < 30 -> {
                    res.text = "BODY TYPE:Overweight"
                }
                else -> {
                    res.text = "BODY TYPE:Obese"
                }
            }
            val msg: String = when {
                bmi < 18 -> "Underweight"
                bmi in 18f..25f -> "Normal"
                bmi in 25f..30f -> "Overweight"
                else -> "Obese"
            }


            Toast.makeText(this, msg, Toast.LENGTH_LONG).show()

            }


    }
    }


activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/calbtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="176dp"
        android:layout_marginTop="96dp"
        android:text="Calculate"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/number2box" />

    <EditText
        android:id="@+id/number2box"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="292dp"
        android:ems="10"
        android:hint="ENTER THE WEIGHT"
        android:inputType="text"
        android:textColor="#2196F3"
        android:textColorHint="#2C2828"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.885"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="48dp"
        android:layout_marginTop="220dp"
        android:text="HEIGHT"
        app:layout_constraintBottom_toBottomOf="@+id/number1box"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="48dp"
        android:layout_marginTop="292dp"
        android:text="WEIGHT"
        app:layout_constraintBottom_toBottomOf="@+id/number2box"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.692" />

    <EditText
        android:id="@+id/number1box"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="196dp"
        android:ems="10"
        android:hint="ENTER THE HEIGHT"
        android:inputType="text"
        android:textColor="#03A9F4"
        android:textColorHint="#3A3737"
        android:textColorLink="#0C87E9"
        app:layout_constraintBottom_toTopOf="@+id/number2box"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.88"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0" />

    <TextView
        android:id="@+id/outputbox"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="56dp"
        android:layout_marginEnd="100dp"
        android:text="RESULT"
        android:textSize="20sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/calbtn" />

    <TextView
        android:id="@+id/conc"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="80dp"
        android:text="BODY TYPE"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.761"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/outputbox" />

    <TextView
        android:id="@+id/conc"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="96dp"
        android:layout_marginTop="120dp"
        android:text="BMI CALCULATOR"
        android:textColor="#5E24C7"
        android:textColorLink="#2439AD"
        android:textSize="24sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>


02-intent

Main Activity.kt
package com.example.mad_lab_ex2

import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.CheckBox
import android.widget.EditText
import android.widget.RadioGroup
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import android.widget.Switch
import android.widget.Spinner
import android.widget.Button
import android.content.Intent
import android.widget.RadioButton

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        var userName: EditText = findViewById(R.id.username)
        var pass: EditText = findViewById(R.id.Pass)
        var switch: Switch = findViewById(R.id.switch1)
        var spinner: Spinner = findViewById(R.id.spinner)
        var radioGroup: RadioGroup = findViewById(R.id.radioGroup)
        var rfc: EditText = findViewById(R.id.rfc)
        var cb1: CheckBox = findViewById(R.id.cb1)
        var cb2: CheckBox = findViewById(R.id.cb2)
        var cb3: CheckBox = findViewById(R.id.cb3)
        var cb4: CheckBox = findViewById(R.id.cb4)
        var btn: Button = findViewById(R.id.button)
        val items = arrayOf("TamilNadu", "Kerala", "AndraPradesh", "North", "NRI")
        var arrayAdapter: ArrayAdapter<String> =
            ArrayAdapter(this, android.R.layout.simple_spinner_item, items)
        arrayAdapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        spinner.adapter = arrayAdapter
        btn.setOnClickListener {
            var myintent: Intent = Intent(this,SecondActivity::class.java).apply {
                putExtra("username", userName.text.toString())
                putExtra("password", pass.getText().toString())
                if (switch.isChecked) {
                    putExtra("Hostellite", "Yes")
                } else {
                    putExtra("Hostellite", "No")
                }
                putExtra("Mess", spinner.selectedItem.toString())
                var id:Int=radioGroup.checkedRadioButtonId
                if(id!=-1) {
                var selectedradio: RadioButton = findViewById(id)
                putExtra("VegNon", selectedradio.text.toString())

                }
                putExtra("reason", rfc.getText().toString())
                var selectedallergies = mutableListOf<String>()
                if (cb1.isChecked) {
                    selectedallergies.add(cb1.getText().toString())
                }
                if (cb2.isChecked) {
                    selectedallergies.add(cb2.getText().toString())
                }
                if (cb3.isChecked) {
                    selectedallergies.add(cb3.getText().toString())
                }
                if (cb4.isChecked) {
                    selectedallergies.add(cb4.getText().toString())
                }
                putExtra("Allergies", selectedallergies.toString())

            }
            startActivity(myintent)
        }
    }
}
SecondActivity.kt
package com.example.mad_lab_ex2

import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.CheckBox
import android.widget.EditText
import android.widget.RadioGroup
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import android.widget.Switch
import android.widget.Spinner
import android.widget.Button
import android.content.Intent
import android.widget.RadioButton
import android.widget.TextView

class SecondActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)
        val user: TextView = findViewById(R.id.userName)
        val hostel: TextView = findViewById(R.id.hostellite)
        val mess: TextView = findViewById(R.id.mess)
        val veg: TextView = findViewById(R.id.veg)
        val reason1: TextView = findViewById(R.id.reason)
        val allergies: TextView = findViewById(R.id.allergies)
        var data: Bundle? = intent.extras
        data?.let {
            user.text = it.getString("username")
            hostel.text =it.getString("Hostellite")
            mess.text = it.getString("Mess")
            veg.text = it.getString("VegNon")
            reason1.text = it.getString("reason")
            allergies.text = it.getString("Allergies")

        }
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="68dp"
        android:text="Mess Management System"
        android:textSize="20sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="52dp"
        android:layout_marginTop="28dp"
        android:text="UserName:"
        android:textSize="16sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView2" />

    <ImageView
        android:id="@+id/imageView2"
        android:layout_width="251dp"
        android:layout_height="130dp"
        android:layout_marginTop="8dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        app:srcCompat="@drawable/foodex2" />

    <EditText
        android:id="@+id/username"
        android:layout_width="213dp"
        android:layout_height="44dp"
        android:layout_marginStart="12dp"
        android:layout_marginTop="8dp"
        android:ems="10"
        android:hint="Enter the Name"
        android:inputType="text"
        app:layout_constraintBottom_toBottomOf="@+id/textView2"
        app:layout_constraintStart_toEndOf="@+id/textView2"
        app:layout_constraintTop_toBottomOf="@+id/imageView2"
        app:layout_constraintVertical_bias="0.0" />

    <EditText
        android:id="@+id/Pass"
        android:layout_width="193dp"
        android:layout_height="44dp"
        android:layout_marginEnd="64dp"
        android:ems="10"
        android:hint="Enter the Password"
        android:inputType="textPassword"
        app:layout_constraintBottom_toBottomOf="@+id/textView3"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/username"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="57dp"
        android:layout_marginTop="44dp"
        android:layout_marginEnd="16dp"
        android:text="Password:"
        android:textSize="16sp"
        app:layout_constraintEnd_toStartOf="@+id/Pass"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="5dp"
        android:text="Hostellite:"
        android:textSize="16sp"
        app:layout_constraintEnd_toEndOf="@+id/textView3"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <TextView
        android:id="@+id/textView8"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="60dp"
        android:layout_marginTop="32dp"
        android:text="Allergies:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView7" />

    <RadioGroup
        android:id="@+id/radioGroup"
        android:layout_width="189dp"
        android:layout_height="46dp"
        android:layout_marginStart="24dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="75dp"
        android:orientation="horizontal"
        app:layout_constraintBottom_toBottomOf="@+id/textView6"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView6"
        app:layout_constraintTop_toBottomOf="@+id/spinner"
        app:layout_constraintVertical_bias="0.533">

        <RadioButton
            android:id="@+id/rb1"
            android:layout_width="84dp"
            android:layout_height="wrap_content"
            android:text="Veg" />

        <RadioButton
            android:id="@+id/rb2"
            android:layout_width="152dp"
            android:layout_height="29dp"
            android:layout_weight="1"
            android:text="Non-Veg" />

    </RadioGroup>

    <Switch
        android:id="@+id/switch1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:text="No"
        android:textSize="14sp"
        app:layout_constraintBottom_toBottomOf="@+id/textView4"
        app:layout_constraintStart_toEndOf="@+id/textView4"
        app:layout_constraintTop_toBottomOf="@+id/Pass"
        app:layout_constraintVertical_bias="1.0" />

    <CheckBox
        android:id="@+id/cb4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="56dp"
        android:text="None"
        app:layout_constraintBottom_toBottomOf="@+id/cb3"
        app:layout_constraintStart_toEndOf="@+id/cb3"
        app:layout_constraintTop_toBottomOf="@+id/cb2"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="64dp"
        android:layout_marginTop="32dp"
        android:layout_marginEnd="24dp"
        android:text="Veg/Non:"
        app:layout_constraintEnd_toStartOf="@+id/radioGroup"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView5" />

    <TextView
        android:id="@+id/textView10"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="56dp"
        android:layout_marginTop="12dp"
        android:text="Yes"
        android:textSize="16sp"
        app:layout_constraintStart_toStartOf="@+id/switch1"
        app:layout_constraintTop_toBottomOf="@+id/Pass" />

    <EditText
        android:id="@+id/rfc"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="54dp"
        android:layout_marginBottom="8dp"
        android:ems="10"
        android:gravity="start|top"
        android:inputType="textMultiLine"
        app:layout_constraintBottom_toBottomOf="@+id/textView7"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView7"
        app:layout_constraintTop_toBottomOf="@+id/radioGroup"
        app:layout_constraintVertical_bias="1.0" />

    <CheckBox
        android:id="@+id/cb3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="36dp"
        android:layout_marginTop="4dp"
        android:text="Nuts"
        app:layout_constraintStart_toEndOf="@+id/textView8"
        app:layout_constraintTop_toBottomOf="@+id/cb1" />

    <TextView
        android:id="@+id/textView7"
        android:layout_width="57dp"
        android:layout_height="51dp"
        android:layout_marginStart="61dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="24dp"
        android:text="Reason for Choice:"
        app:layout_constraintEnd_toStartOf="@+id/rfc"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView6" />

    <CheckBox
        android:id="@+id/cb1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginTop="16dp"
        android:text="Milk"
        app:layout_constraintStart_toEndOf="@+id/textView8"
        app:layout_constraintTop_toBottomOf="@+id/rfc" />

    <CheckBox
        android:id="@+id/cb2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="60dp"
        android:text="Soy"
        app:layout_constraintBottom_toBottomOf="@+id/cb1"
        app:layout_constraintStart_toEndOf="@+id/cb1"
        app:layout_constraintTop_toBottomOf="@+id/rfc"
        app:layout_constraintVertical_bias="0.916" />

    <Spinner
        android:id="@+id/spinner"
        android:layout_width="182dp"
        android:layout_height="23dp"
        android:layout_marginTop="24dp"
        android:layout_marginEnd="72dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/switch1" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="Submit"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/cb4" />

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="60dp"
        android:layout_marginTop="24dp"
        android:text="Mess:"
        android:textSize="16sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

</androidx.constraintlayout.widget.ConstraintLayout>

activity_main2.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#C6E7EB">

    <TextView
        android:id="@+id/textView9"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="68dp"
        android:text="Mess Management System"
        android:textSize="20sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView11"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="74dp"
        android:text="UserName:"
        app:layout_constraintBaseline_toBaselineOf="@+id/userName"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/allergies"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="35dp"
        android:layout_marginTop="26dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView16"
        app:layout_constraintTop_toBottomOf="@+id/reason" />

    <TextView
        android:id="@+id/textView15"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:layout_marginEnd="4dp"
        android:text="Reason:"
        app:layout_constraintEnd_toEndOf="@+id/textView14"
        app:layout_constraintTop_toBottomOf="@+id/textView14" />

    <TextView
        android:id="@+id/textView16"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="74dp"
        android:text="Allergies:"
        app:layout_constraintBaseline_toBaselineOf="@+id/allergies"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/userName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="330dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView11"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/mess"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="31dp"
        android:text="TextView"
        app:layout_constraintStart_toStartOf="@+id/veg"
        app:layout_constraintTop_toBottomOf="@+id/hostellite" />

    <TextView
        android:id="@+id/hostellite"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="28dp"
        android:text="TextView"
        app:layout_constraintStart_toStartOf="@+id/userName"
        app:layout_constraintTop_toBottomOf="@+id/userName" />

    <TextView
        android:id="@+id/textView13"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="1dp"
        android:layout_marginBottom="29dp"
        android:text="Mess:"
        app:layout_constraintBottom_toTopOf="@+id/textView14"
        app:layout_constraintStart_toStartOf="@+id/textView14" />

    <TextView
        android:id="@+id/textView14"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="34dp"
        android:text="Veg/Non:"
        app:layout_constraintBaseline_toBaselineOf="@+id/veg"
        app:layout_constraintEnd_toStartOf="@+id/veg" />

    <TextView
        android:id="@+id/veg"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="29dp"
        android:layout_marginEnd="2dp"
        android:text="TextView"
        app:layout_constraintEnd_toEndOf="@+id/reason"
        app:layout_constraintTop_toBottomOf="@+id/mess" />

    <TextView
        android:id="@+id/reason"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="26dp"
        android:layout_marginEnd="1dp"
        android:text="TextView"
        app:layout_constraintEnd_toEndOf="@+id/allergies"
        app:layout_constraintTop_toBottomOf="@+id/veg" />

    <TextView
        android:id="@+id/textView12"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hostellite"
        app:layout_constraintBaseline_toBaselineOf="@+id/hostellite"
        app:layout_constraintStart_toStartOf="@+id/textView11" />

    <ImageView
        android:id="@+id/imageView3"
        android:layout_width="225dp"
        android:layout_height="146dp"
        android:layout_marginTop="69dp"
        android:layout_marginBottom="66dp"
        app:layout_constraintBottom_toBottomOf="@+id/textView11"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="@+id/textView9"
        app:srcCompat="@drawable/foodex2" />

</androidx.constraintlayout.widget.ConstraintLayout>

AndroidManifest.xml
<activity
    android:name=".SecondActivity"
    android:exported="true" />

03-listview

MainActivity.kt
import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.ListView
import android.widget.Toast
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val mylistview: ListView = findViewById(R.id.mylistview)

        // Create a list of persons
        val persons = listOf(
            Person("101",  50,"52",R.drawable.f1),
            Person("202",  60,"60",R.drawable.f2),
            Person("303",  45,"100",R.drawable.f3),
            Person("404",  55,"123",R.drawable.f44),
            Person("505", 40,"90",R.drawable.f5),

            )

        // Set the custom adapter
        val adapter = PersonAdapter(this, R.layout.list_item, persons)
        mylistview.adapter = adapter

        // Handle item click
        mylistview.setOnItemClickListener { parent, view, position, id ->
            val selectedPerson = persons[position]
            Toast.makeText(
                this,
                "Item ID: ${selectedPerson.name}, price: ${selectedPerson.age}, qty: ${selectedPerson.gender}",
                Toast.LENGTH_LONG
            ).show()
        }
    }
}

Person.kt

data class Person(val name: String, val age: Int, val gender: String,val imageResId: Int)


PersonAdapter.kt

import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.ArrayAdapter
import android.widget.ImageView
import android.widget.TextView

class PersonAdapter(context: Context, private val resource: Int, private val persons: List<Person>) :
    ArrayAdapter<Person>(context, resource, persons) {

    override fun getView(position: Int, convertView: View?, parent: ViewGroup): View {
        val view = convertView ?: LayoutInflater.from(context).inflate(resource, parent, false)

        // Get current person
        val person = persons[position]

        // Get TextViews from layout
        val nameTextView: TextView = view.findViewById(R.id.busName)
        val ageTextView: TextView = view.findViewById(R.id.busCapacity)
        val genderTextView: TextView = view.findViewById(R.id.busRoute)
        val busImage = view.findViewById<ImageView>(R.id.busImage)


        // Set data to the TextViews
        nameTextView.text = person.name
        ageTextView.text = "price: ${person.age}"
        genderTextView.text = "qty: ${person.gender}"
        busImage.setImageResource(person.imageResId)
        return view
    }
}


activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <ListView
        android:id="@+id/mylistview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:dividerHeight="1dp"
        android:divider="@android:color/darker_gray" />

</LinearLayout>



list_item.xml

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="horizontal"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="10dp">

    <ImageView
        android:id="@+id/busImage"
        android:layout_width="60dp"
        android:layout_height="60dp"
        android:layout_marginEnd="10dp"
        />

    <LinearLayout
        android:orientation="vertical"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <TextView
            android:id="@+id/busName"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="18sp"
            android:textStyle="bold"/>

        <TextView
            android:id="@+id/busRoute"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>
    </LinearLayout>

    <TextView
        android:id="@+id/busCapacity"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />
</LinearLayout>



04-Database

MainActivity.kt

import android.database.Cursor
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.ListView
import android.widget.SimpleCursorAdapter
import android.widget.Toast
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
class MainActivity : AppCompatActivity() {

    private lateinit var database: Database
    private lateinit var cursor: Cursor

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }

        // Initialize the database
        database = Database(this)

        // Get references to UI elements
        val busNumberField: EditText = findViewById(R.id.busNumber)
        val routeField: EditText = findViewById(R.id.route)
        val capacityField: EditText = findViewById(R.id.capacity)
        val saveBtn: Button = findViewById(R.id.save)
        val viewBtn: Button = findViewById(R.id.view)
        val deleteBtn: Button = findViewById(R.id.delete)
        val updateBtn: Button = findViewById(R.id.update)
        val listView: ListView = findViewById(R.id.listview)

        // Save button onClick listener to save the bus record
        saveBtn.setOnClickListener {
            val busNumber = busNumberField.text.toString().trim()
            val route = routeField.text.toString().trim()
            val capacity = capacityField.text.toString().trim().toIntOrNull()
            if (busNumber.isNotEmpty() && route.isNotEmpty() && capacity != null) {
                database.saveBus(busNumber, route, capacity)
                busNumberField.text.clear()
                routeField.text.clear()
                capacityField.text.clear()
            } else {
                Toast.makeText(this, "Please enter valid data", Toast.LENGTH_SHORT).show()
            }
        }

        // View button onClick listener to display all bus records
        viewBtn.setOnClickListener {
            cursor = database.viewAllBuses() // Retrieve all buses

            if (cursor.count == 0) {
                Toast.makeText(this, "No records found", Toast.LENGTH_SHORT).show()
                return@setOnClickListener
            }

            val columns = arrayOf("bus_number", "route", "capacity")
            val views = intArrayOf(R.id.busNumberView, R.id.routeView, R.id.capacityView)

            val cursorAdapter = SimpleCursorAdapter(
                this,
                R.layout.list_item,
                cursor,
                columns,
                views,
                0
            )

            listView.adapter = cursorAdapter
        }

        // Delete button onClick listener to delete the bus record
        deleteBtn.setOnClickListener {
            val busNumber = busNumberField.text.toString().trim()
            if (busNumber.isNotEmpty()) {
                val rowsDeleted = database.deleteBus(busNumber)
                if (rowsDeleted > 0) {
                    Toast.makeText(this, "Record deleted", Toast.LENGTH_SHORT).show()
                    refreshListView()
                } else {
                    Toast.makeText(this, "Record not found", Toast.LENGTH_SHORT).show()
                }
                busNumberField.text.clear()
            } else {
                Toast.makeText(this, "Please enter a valid bus number", Toast.LENGTH_SHORT).show()
            }
        }

        // Update button onClick listener to update the bus record
        updateBtn.setOnClickListener {
            val busNumber = busNumberField.text.toString().trim()
            val route = routeField.text.toString().trim()
            val capacity = capacityField.text.toString().trim().toIntOrNull()
            if (busNumber.isNotEmpty() && route.isNotEmpty() && capacity != null) {
                val rowsUpdated = database.updateBus(busNumber, route, capacity)
                if (rowsUpdated > 0) {
                    Toast.makeText(this, "Record updated", Toast.LENGTH_SHORT).show()
                    refreshListView()
                } else {
                    Toast.makeText(this, "Record not found", Toast.LENGTH_SHORT).show()
                }
            } else {
                Toast.makeText(this, "Please enter valid data", Toast.LENGTH_SHORT).show()
            }
        }
        val searchBtn: Button = findViewById(R.id.search)

        searchBtn.setOnClickListener {
            val busNumber = busNumberField.text.toString().trim()
            if (busNumber.isNotEmpty()) {
                val cursor = database.findBus(busNumber)

                if (cursor.moveToFirst()) {
                    val route = cursor.getString(cursor.getColumnIndexOrThrow("route"))
                    val capacity = cursor.getInt(cursor.getColumnIndexOrThrow("capacity"))

                    // Populate fields with the found data
                    busNumberField.setText(busNumber)
                    routeField.setText(route)
                    capacityField.setText(capacity.toString())

                    Toast.makeText(this, "Bus found", Toast.LENGTH_SHORT).show()
                } else {
                    Toast.makeText(this, "No matching record found", Toast.LENGTH_SHORT).show()
                }

                cursor.close()
            } else {
                Toast.makeText(this, "Please enter a bus number to search", Toast.LENGTH_SHORT).show()
            }
        }




        // ListView item click listener to handle clicks on items in the list
        listView.setOnItemClickListener { _, _, position, _ ->
            cursor.moveToPosition(position)
            val busNumber = cursor.getString(cursor.getColumnIndexOrThrow("bus_number"))
            val route = cursor.getString(cursor.getColumnIndexOrThrow("route"))
            val capacity = cursor.getInt(cursor.getColumnIndexOrThrow("capacity"))

            busNumberField.setText(busNumber)
            routeField.setText(route)
            capacityField.setText(capacity.toString())
        }
    }

    private fun refreshListView() {
        cursor = database.viewAllBuses()
        val columns = arrayOf("bus_number", "route", "capacity")
        val views = intArrayOf(R.id.busNumberView, R.id.routeView, R.id.capacityView)

        val cursorAdapter = SimpleCursorAdapter(
            this,
            R.layout.list_item,
            cursor,
            columns,
            views,
            0
        )

        findViewById<ListView>(R.id.listview).adapter = cursorAdapter
    }

    override fun onDestroy() {
        super.onDestroy()
        if (::cursor.isInitialized) {
            cursor.close()
        }
    }
}

Database.kt


import android.content.ContentValues
import android.content.Context
import android.database.Cursor
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper
private const val DB_NAME = "BusManagement"
private const val DB_VERSION = 1

class Database(context: Context) : SQLiteOpenHelper(context, DB_NAME, null, DB_VERSION) {

    companion object {
        private const val TABLE_BUS = "bus"
        private const val COLUMN_ID = "_id"
        private const val COLUMN_BUS_NUMBER = "bus_number"
        private const val COLUMN_ROUTE = "route"
        private const val COLUMN_CAPACITY = "capacity"
    }

    override fun onCreate(db: SQLiteDatabase) {
        val createTableQuery = """
            CREATE TABLE $TABLE_BUS (
                $COLUMN_ID INTEGER PRIMARY KEY AUTOINCREMENT,
                $COLUMN_BUS_NUMBER TEXT UNIQUE,
                $COLUMN_ROUTE TEXT,
                $COLUMN_CAPACITY INTEGER
            )
        """.trimIndent()

        db.execSQL(createTableQuery)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        if (oldVersion < newVersion) {
            db.execSQL("DROP TABLE IF EXISTS $TABLE_BUS")
            onCreate(db)
        }
    }

    fun viewAllBuses(): Cursor {
        val db = readableDatabase
        return db.rawQuery("SELECT * FROM $TABLE_BUS", null)
    }

    fun saveBus(busNumber: String, route: String, capacity: Int) {
        val db = writableDatabase
        val values = ContentValues().apply {
            put(COLUMN_BUS_NUMBER, busNumber)
            put(COLUMN_ROUTE, route)
            put(COLUMN_CAPACITY, capacity)
        }

        try {
            db.insert(TABLE_BUS, null, values)
        } catch (e: Exception) {
            // Handle the exception (e.g., log it)
        }
    }

    fun findBus(busNumber: String): Cursor {
        val db = readableDatabase
        return db.rawQuery(
            "SELECT * FROM $TABLE_BUS WHERE $COLUMN_BUS_NUMBER = ?",
            arrayOf(busNumber)
        )
    }

    fun updateBus(busNumber: String, route: String, capacity: Int): Int {
        val db = writableDatabase
        val values = ContentValues().apply {
            put(COLUMN_ROUTE, route)
            put(COLUMN_CAPACITY, capacity)
        }

        return db.update(
            TABLE_BUS,
            values,
            "$COLUMN_BUS_NUMBER = ?",
            arrayOf(busNumber)
        )
    }

    fun deleteBus(busNumber: String): Int {
        val db = writableDatabase
        return db.delete(
            TABLE_BUS,
            "$COLUMN_BUS_NUMBER = ?",
            arrayOf(busNumber)
        )
    }
}

acivity_main
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="BUS DETAILS"
        android:textColor="#CA1616"
        android:textSize="20sp" />

    <EditText
        android:id="@+id/busNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="ENTER THE BUS NUMBER" />

    <EditText
        android:id="@+id/route"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="ENTER THE ROUTE TAKEN" />

    <EditText
        android:id="@+id/capacity"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="number"
        android:hint="ENTER THE CAPACITY" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/save"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Save" />

        <Button
            android:id="@+id/view"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="View" />

        <Button
            android:id="@+id/delete"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Delete" />

        <Button
            android:id="@+id/update"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Update" />
    </LinearLayout>


    <Button
        android:id="@+id/search"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Search" />


    <ListView
        android:id="@+id/listview"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1" />
</LinearLayout>



list_item.xml


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:padding="8dp">

    <TextView
        android:id="@+id/busNumberView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@android:color/holo_red_dark"
        android:textSize="16sp"
        android:textStyle="bold" />

    <TextView
        android:id="@+id/routeView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@android:color/holo_red_dark"
        android:textSize="14sp" />

    <TextView
        android:id="@+id/capacityView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@android:color/holo_red_dark"
        android:textSize="14sp" />
</LinearLayout>


05 -  Calling ContentProvider
MainActivity.kt
package com.example.madlab_ex5
import android.content.Intent
import android.content.pm.PackageManager
import android.database.Cursor
import android.net.Uri
import android.os.Bundle
import android.provider.ContactsContract
import android.widget.ArrayAdapter
import android.widget.Button
import android.widget.ListView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat
class MainActivity : AppCompatActivity() {
    private val REQUEST_READ_CONTACTS = 1
    private val REQUEST_CALL_PHONE = 2
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val loadbtn: Button = findViewById(R.id.loadbtn)
        val listView: ListView = findViewById(R.id.listView)
        // Check and request permission to read contacts if not already granted
        if (checkSelfPermission(android.Manifest.permission.READ_CONTACTS) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, arrayOf(android.Manifest.permission.READ_CONTACTS), REQUEST_READ_CONTACTS)
        }
        loadbtn.setOnClickListener {
            val contactList = mutableListOf<String>()
            val contactNumbers = mutableListOf<String>()  // To store phone numbers separately
            val cursor: Cursor? = contentResolver.query(
                ContactsContract.CommonDataKinds.Phone.CONTENT_URI,
                null,
                null,
                null,
                ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME + " ASC"
            )
            if (cursor != null) {
                while (cursor.moveToNext()) {
                    val name = cursor.getString(cursor.getColumnIndexOrThrow(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME))
                    val number = cursor.getString(cursor.getColumnIndexOrThrow(ContactsContract.CommonDataKinds.Phone.NUMBER))
                    contactList.add("$name \n $number")
                    contactNumbers.add(number)  // Store phone number separately
                }
                cursor.close()}
            val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, contactList)
            listView.adapter = adapter
            // Set an item click listener to make a call when a contact is selected
            listView.setOnItemClickListener { _, _, position, _ ->
                val selectedNumber = contactNumbers[position]
                makeCall(selectedNumber) }}}
    // Function to make a call
    private fun makeCall(phoneNumber: String) {
        if (checkSelfPermission(android.Manifest.permission.CALL_PHONE) != PackageManager.PERMISSION_GRANTED) {
            // Request CALL_PHONE permission if not granted
            ActivityCompat.requestPermissions(this, arrayOf(android.Manifest.permission.CALL_PHONE), REQUEST_CALL_PHONE)
            return
        }
        // Use an intent to initiate a phone call
        val callIntent = Intent(Intent.ACTION_CALL)
        callIntent.data = Uri.parse("tel:$phoneNumber")
        try {
            startActivity(callIntent)
        } catch (e: Exception) {
            Toast.makeText(this, "Unable to make the call", Toast.LENGTH_SHORT).show() }
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"

    android:orientation="vertical"
    >
    <TextView
        android:layout_marginTop="30dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="CONTACTS"
        android:textSize="20dp"
        android:layout_gravity="center_horizontal"
        android:textColor="#D81B60"
        />
    <Button
        android:id="@+id/loadbtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Load Contacts"
        android:layout_marginTop="20dp"
        />
    <ListView
        android:id="@+id/listView"
        android:layout_width="378dp"
        android:layout_height="match_parent"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="20dp"
        />
</LinearLayout>
AndroidManifest.xml
<uses-feature
    android:name="android.hardware.telephony"
    android:required="false" />

<uses-permission android:name="android.permission.READ_CONTACTS"/>
<uses-permission android:name="android.permission.CALL_PHONE" />


06 - BroadcastReciever: airplane mode, battery level
MainActivity.kt
package com.example.mad_lab_ex6

import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.content.IntentFilter
import android.os.Bundle
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    private lateinit var myReceiver: MyBroadCastReceiver
    private lateinit var myreceiver2: MyBatBroadCastReceiver
    private lateinit var airplaneModeTextView: TextView
    private lateinit var BatTextView: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        airplaneModeTextView = findViewById(R.id.t1)
        BatTextView=findViewById(R.id.t2)
        val intentFilter = IntentFilter(Intent.ACTION_AIRPLANE_MODE_CHANGED)
        val intentFilter2 = IntentFilter(Intent.ACTION_BATTERY_CHANGED)

        myReceiver = MyBroadCastReceiver(airplaneModeTextView)
        registerReceiver(myReceiver, intentFilter)
        myreceiver2= MyBatBroadCastReceiver(BatTextView)
        registerReceiver(myreceiver2,intentFilter2)
    }

    override fun onDestroy() {
        super.onDestroy()
        unregisterReceiver(myReceiver)
    }
}
class MyBroadCastReceiver(private val textView: TextView) : BroadcastReceiver() {
    override fun onReceive(context: Context?, intent: Intent?) {
        if (intent?.action == Intent.ACTION_AIRPLANE_MODE_CHANGED) {
            val isAirplaneModeOn = intent.getBooleanExtra("state", false)
            textView.text = if (isAirplaneModeOn) {
                "Airplane Mode is ON"
            } else {
                "Airplane Mode is OFF"
            }
            if(isAirplaneModeOn){
                Toast.makeText(context,"Airplane Mode is on",Toast.LENGTH_LONG).show()
            }
            else{
                Toast.makeText(context,"Airplane Mode is off",Toast.LENGTH_LONG).show()
            }
        }
    }
}
class MyBatBroadCastReceiver(private val textView: TextView) : BroadcastReceiver() {
    override fun onReceive(context: Context?, intent: Intent?) {
        if (intent?.action == Intent.ACTION_BATTERY_CHANGED) {
            val batteryLevel = intent.getIntExtra("level", -1)
            val statusText = when {
                batteryLevel == 100 -> {
                    Toast.makeText(context, "Full Charge", Toast.LENGTH_LONG).show()
                    "Full Charge"
                }
                batteryLevel <= 20 -> {
                    Toast.makeText(context, "Battery Low", Toast.LENGTH_LONG).show()
                    "Battery Low"
                }
                else -> {
                    Toast.makeText(context, "Battery Level: $batteryLevel%", Toast.LENGTH_LONG).show()

                    "Battery Level: $batteryLevel%"

                }
            }
            textView.text = statusText
        }
    }
}
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:layout_gravity="center">
    <TextView
        android:id="@+id/t1"
        android:textSize="20dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:gravity="center"/>
    <TextView
        android:id="@+id/t2"
        android:textSize="20dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:gravity="center"/>
</LinearLayout>


</LinearLayout>
AndroidManifest.xml
(after activity before /application)
<receiver android:name="MyBroadCastReceiver"
    android:enabled="true" android:exported="false">
    <intent-filter>
        <action
            android:name="android.intent.action.AIRPLANE_MODE_CHANGED"/>
    </intent-filter>
</receiver>
<receiver android:name="MyBatBroadCastReceiver"
    android:enabled="true" android:exported="false">
    <intent-filter>
        <action
            android:name="android.intent.action.BATTERY_CHANGED"/>
    </intent-filter>
</receiver>

06-Broadcast sms

MainActivity.kt

import android.Manifest
import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.content.IntentFilter
import android.content.pm.PackageManager
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.text.TextUtils
import android.util.Log
import android.widget.TextView
import androidx.core.app.ActivityCompat
import androidx.localbroadcastmanager.content.LocalBroadcastManager

class MainActivity : AppCompatActivity() {
    private val SMS_PERMISSION_CODE = 100
    private lateinit var textViewSms: TextView

    private val smsReceiver = object : BroadcastReceiver() {
        override fun onReceive(context: Context?, intent: Intent?) {
            val message = intent?.getStringExtra("message")
            if (!TextUtils.isEmpty(message)) {
                textViewSms.text = message
            }
        }
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        textViewSms = findViewById(R.id.textViewSms)

        // Check for SMS permissions
        if (ActivityCompat.checkSelfPermission(this, Manifest.permission.RECEIVE_SMS) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.RECEIVE_SMS), SMS_PERMISSION_CODE)
        }

        // Register the local broadcast receiver
        LocalBroadcastManager.getInstance(this).registerReceiver(smsReceiver, IntentFilter("SmsMessageReceived"))
    }

    override fun onDestroy() {
        super.onDestroy()
        // Unregister the local broadcast receiver
        LocalBroadcastManager.getInstance(this).unregisterReceiver(smsReceiver)
    }
}


SmsReceiver.kt


import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.os.Bundle
import android.telephony.SmsMessage
import android.util.Log
import androidx.localbroadcastmanager.content.LocalBroadcastManager

class SmsReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context, intent: Intent) {
        // Check if the received intent is for SMS messages
        if (intent.action == "android.provider.Telephony.SMS_RECEIVED") {
            // Retrieve the SMS message received
            val bundle: Bundle? = intent.extras
            if (bundle != null) {
                val pdus = bundle.get("pdus") as Array<*>
                for (i in pdus.indices) {
                    val smsMessage = SmsMessage.createFromPdu(pdus[i] as ByteArray)
                    val sender = smsMessage.displayOriginatingAddress
                    val messageBody = smsMessage.messageBody

                    // Log or handle the incoming SMS
                    Log.d("SmsReceiver", "Sender: $sender, Message: $messageBody")

                    // Send the message to MainActivity
                    val smsIntent = Intent("SmsMessageReceived")
                    smsIntent.putExtra("message", messageBody)
                    LocalBroadcastManager.getInstance(context).sendBroadcast(smsIntent)
                }
            }
        }
    }
}


activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/textViewSms"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="No messages yet"
        android:textSize="18sp" />

</LinearLayout>


manifest

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <!-- Permissions to receive and read SMS -->
    <uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />

    <uses-permission android:name="android.permission.RECEIVE_SMS" />
    <uses-permission android:name="android.permission.READ_SMS" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Broadcastsms"
        tools:targetApi="31">

        <!-- Main Activity -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- BroadcastReceiver for SMS_RECEIVED -->
        <receiver android:name=".SmsReceiver" android:exported="true" android:permission="android.permission.BROADCAST_SMS">
            <intent-filter>
                <action android:name="android.provider.Telephony.SMS_RECEIVED" />
            </intent-filter>
        </receiver>

    </application>

</manifest>

07-music service


MainActivity.kt


import android.content.Intent
import android.net.Uri
import android.os.Bundle
import android.widget.Button
import android.widget.VideoView
import androidx.appcompat.app.AppCompatActivity
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val btnStartAudio = findViewById<Button>(R.id.btnStartAudio)
        val btnStopAudio = findViewById<Button>(R.id.btnStopAudio)

        btnStartAudio.setOnClickListener {
            val intent = Intent(this, MediaPlayerService::class.java)
            startService(intent)
        }

        btnStopAudio.setOnClickListener {
            val intent = Intent(this, MediaPlayerService::class.java)
            stopService(intent)
        }

        val videoView = findViewById<VideoView>(R.id.videoView)
        val videoUri = Uri.parse("android.resource://${packageName}/${R.raw.video}")
        videoView.setVideoURI(videoUri)

        val btnPlayVideo = findViewById<Button>(R.id.btnPlayVideo)
        val btnPauseVideo = findViewById<Button>(R.id.btnPauseVideo)

        btnPlayVideo.setOnClickListener {
            videoView.start()
        }

        btnPauseVideo.setOnClickListener {
            videoView.pause()
        }
    }
}

MediaPlayerService.kt



import android.app.Service
import android.content.Intent
import android.media.MediaPlayer
import android.os.IBinder
import android.util.Log

class MediaPlayerService : Service() {

    private lateinit var mediaPlayer: MediaPlayer

    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        mediaPlayer = MediaPlayer.create(this, R.raw.music)

        mediaPlayer.start()

        Log.d("media player started running","audio started")

        return START_STICKY
    }

    override fun onDestroy() {

        if (mediaPlayer.isPlaying) {
            mediaPlayer.stop()
            mediaPlayer.release()
        }
        Log.d("MediaPlayerService", "Audio stopped")
        super.onDestroy()
    }

    override fun onBind(intent: Intent?): IBinder? {
        return null
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- Button to start audio playback -->
    <Button
        android:id="@+id/btnStartAudio"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Start Audio"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp" />

    <!-- Button to stop audio playback -->
    <Button
        android:id="@+id/btnStopAudio"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Stop Audio"
        app:layout_constraintTop_toBottomOf="@id/btnStartAudio"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp" />

    <!-- VideoView for video playback -->
    <VideoView
        android:id="@+id/videoView"
        android:layout_width="0dp"
        android:layout_height="250dp"
        android:layout_marginTop="32dp"
        app:layout_constraintTop_toBottomOf="@id/btnStopAudio"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintWidth_default="spread"
        android:layout_marginBottom="16dp" />

    <!-- Button to play video -->
    <Button
        android:id="@+id/btnPlayVideo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Play Video"
        app:layout_constraintTop_toBottomOf="@id/videoView"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp" />

    <!-- Button to pause video -->
    <Button
        android:id="@+id/btnPauseVideo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Pause Video"
        app:layout_constraintTop_toBottomOf="@id/btnPlayVideo"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp" />

</androidx.constraintlayout.widget.ConstraintLayout>

##androidManifest.xml
 <uses-permission android:name="android.permission.READ_MEDIA_AUDIO"/>
    <uses-permission android:name="android.permission.READ_MEDIA_VIDEO"/>
    <uses-permission android:name="android.permission.WAKE_LOCK"/>
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE"/>


08-sms and phone no

MainActivity.kt

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import android.Manifest
import android.content.pm.PackageManager
import android.telephony.SmsMessage
import android.telephony.gsm.SmsManager
import android.widget.Toast

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val phonefield: EditText = findViewById(R.id.phone)
        val emailfield: EditText = findViewById(R.id.email)
        val feedbackUrl = "https://forms.gle/XWW4xFjNTyQmeViM7"
        val sendbtn: Button = findViewById(R.id.send)

        sendbtn.setOnClickListener {
            if (phonefield.text.isNotEmpty()) {
                if (ActivityCompat.checkSelfPermission(
                        this,
                        Manifest.permission.SEND_SMS
                    ) != PackageManager.PERMISSION_GRANTED
                ) {
                    requestPermissions(arrayOf(Manifest.permission.SEND_SMS), 2)
                } else {
                    val mobilenumber = phonefield.text.toString()
                    val message = "Please fill out our feedback form: $feedbackUrl"
                    val smsManager = SmsManager.getDefault()
                    smsManager.sendTextMessage(mobilenumber, null, message, null, null)
                    Toast.makeText(this, "SMS Sent Successfully", Toast.LENGTH_LONG).show()
                }
            } else if (emailfield.text.isNotEmpty()) {
                val intent = Intent(Intent.ACTION_SEND).apply {
                    type = "message/rfc822"
                    val subject = "Feedback Request"
                    val message = "Please fill out our feedback form: $feedbackUrl"
                    putExtra(Intent.EXTRA_EMAIL, arrayOf(emailfield.text.toString()))
                    putExtra(Intent.EXTRA_SUBJECT, subject)
                    putExtra(Intent.EXTRA_TEXT, message)
                }
                startActivity(Intent.createChooser(intent, "Choose Email App..."))
            }
        }
    }
}


activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/phone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone"
        android:padding="12dp"
        android:layout_marginBottom="16dp"
        android:background="@android:drawable/edit_text" />

    <EditText
        android:id="@+id/email"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Email Address"
        android:inputType="textEmailAddress"
        android:padding="12dp"
        android:layout_marginBottom="16dp"
        android:background="@android:drawable/edit_text" />

    <Button
        android:id="@+id/send"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send FeedBack"
        android:padding="12dp"
        android:backgroundTint="@color/design_default_color_primary"
        android:textColor="@android:color/white" />

</LinearLayout>


Manifest

<uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />
    <uses-permission android:name="android.permission.SEND_SMS"/>

////////////////////////////////////////////////////////////////////////////////

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />
    <uses-permission android:name="android.permission.SEND_SMS"/>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Smsfeedback"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
///////////////////////////////////////////////////////////////////////////////////////

09-bluetooth detect

MainActivity.kt
package com.example.mad_lab_ex9_discover

import android.Manifest
import android.bluetooth.BluetoothAdapter
import android.bluetooth.BluetoothDevice
import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.content.IntentFilter
import android.content.pm.PackageManager
import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.Button
import android.widget.ListView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat
import androidx.core.content.ContextCompat

class MainActivity : AppCompatActivity() {

    private lateinit var bluetoothAdapter: BluetoothAdapter
    private lateinit var deviceListAdapter: ArrayAdapter<String>
    private val discoveredDevices = mutableListOf<String>()

    private val receiver = object : BroadcastReceiver() {
        override fun onReceive(context: Context?, intent: Intent?) {
            when (intent?.action) {
                BluetoothDevice.ACTION_FOUND -> {
                    // A Bluetooth device was found
                    val device: BluetoothDevice? =
                        intent.getParcelableExtra(BluetoothDevice.EXTRA_DEVICE)
                    device?.let {
                        val deviceInfo = "${it.name} - ${it.address}"
                        discoveredDevices.add(deviceInfo)
                        deviceListAdapter.notifyDataSetChanged()
                    }
                }
                BluetoothAdapter.ACTION_DISCOVERY_FINISHED -> {
                    // Discovery process finished
                    Toast.makeText(context, "Discovery finished", Toast.LENGTH_SHORT).show()
                }
            }
        }
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initialize BluetoothAdapter
        bluetoothAdapter = BluetoothAdapter.getDefaultAdapter()

        // Set up ListView to show discovered devices
        val listView: ListView = findViewById(R.id.device_list)
        deviceListAdapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, discoveredDevices)
        listView.adapter = deviceListAdapter

        // Set up Discover Button
        val discoverButton: Button = findViewById(R.id.btn_discover)
        discoverButton.setOnClickListener {
            // Check if Bluetooth is supported
            if (bluetoothAdapter == null) {
                Toast.makeText(this, "Bluetooth not supported", Toast.LENGTH_SHORT).show()
                return@setOnClickListener
            }

            // Request necessary permissions
            if (ContextCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION)
                != PackageManager.PERMISSION_GRANTED) {
                ActivityCompat.requestPermissions(
                    this,
                    arrayOf(Manifest.permission.ACCESS_FINE_LOCATION),
                    1
                )
            } else {
                discoverBluetoothDevices()
            }
        }
    }

    private fun discoverBluetoothDevices() {
        // Start Bluetooth discovery
        if (bluetoothAdapter.isDiscovering) {
            bluetoothAdapter.cancelDiscovery()
        }
        bluetoothAdapter.startDiscovery()

        // Register for broadcast when a device is found
        val filter = IntentFilter(BluetoothDevice.ACTION_FOUND)
        registerReceiver(receiver, filter)

        // Register for broadcast when discovery finishes
        val finishFilter = IntentFilter(BluetoothAdapter.ACTION_DISCOVERY_FINISHED)
        registerReceiver(receiver, finishFilter)

        // Clear previous results
        discoveredDevices.clear()
        deviceListAdapter.notifyDataSetChanged()

        Toast.makeText(this, "Discovery started", Toast.LENGTH_SHORT).show()
    }

    override fun onDestroy() {
        super.onDestroy()
        // Unregister the broadcast receiver
        unregisterReceiver(receiver)
    }
}
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <Button
        android:id="@+id/btn_discover"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Discover Bluetooth Devices" />

    <ListView
        android:id="@+id/device_list"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />
</LinearLayout>

AndroidManifest.xml
<uses-permission android:name="android.permission.BLUETOOTH"/>
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>

<uses-permission android:name="android.permission.BLUETOOTH_SCAN" />

10-fragments

MainActivity.kt

import android.os.Bundle
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.viewpager2.widget.ViewPager2
import com.google.android.material.tabs.TabLayout
import com.google.android.material.tabs.TabLayoutMediator

class MainActivity : AppCompatActivity() {
    private lateinit var tabLayout: TabLayout
    private lateinit var viewPager: ViewPager2

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)

        tabLayout = findViewById(R.id.tabLayout)
        viewPager = findViewById(R.id.viewPager)
        val adapter = ViewPagerAdapter(this)
        viewPager.adapter = adapter

        // Connect TabLayout and ViewPager2
        TabLayoutMediator(tabLayout, viewPager) { tab, position ->
            tab.text = when (position) {
                0 -> "HOME"
                1 -> "MY TRIPS"
                2 -> "PAYMENT DETAILS"
                else -> null
            }
        }.attach()
    }
}

activity_main
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:orientation="vertical"
    android:layout_marginTop="20sp"
    >


    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">
        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"

            android:layout_height="wrap_content"
            android:text="CHATS" />
        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="STATUS" />
        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="CALLS" />
    </com.google.android.material.tabs.TabLayout>
    <androidx.viewpager2.widget.ViewPager2
        android:id="@+id/viewPager"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</LinearLayout>

FragmentOne.kt

import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import androidx.fragment.app.Fragment

class FragmentOne : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container:
    ViewGroup?,savedInstanceState: Bundle?
    ): View? {
        return inflater.inflate(R.layout.fragment_one, container, false)
    }
}


fragment_one.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFFFFF"
    android:padding="16dp">

    <!-- Header Section -->
    <TextView
        android:id="@+id/headerTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:background="#4CAF50"
        android:gravity="center"
        android:padding="16dp"
        android:text="HOME"
        android:textColor="#FFFFFF"
        android:textSize="24sp"
        android:textStyle="bold" />

    <!-- Bus Route Information Section -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:layout_marginTop="16dp">

        <TextView
            android:id="@+id/routeTitle"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Available Bus Routes"
            android:textColor="#000000"
            android:textSize="20sp"
            android:textStyle="bold"
            android:paddingBottom="8dp" />

        <TextView
            android:id="@+id/busRoute1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="BUS 101: Coimbatore (CBE) - Palakkad (PKD)"
            android:textColor="#333333"
            android:textSize="16sp"
            android:padding="8dp"
            android:background="#E0E0E0" />

        <TextView
            android:id="@+id/busRoute2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="BUS 102: Coimbatore (CBE) - Thrissur (TCR)"
            android:textColor="#333333"
            android:textSize="16sp"
            android:padding="8dp"
            android:background="#E0E0E0"
            android:layout_marginTop="4dp" />

    </LinearLayout>

    <!-- Buttons Section -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="24dp">

        <Button
            android:id="@+id/btnBookTicket"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Book Ticket"
            android:textColor="#FFFFFF"
            android:backgroundTint="#1976D2"
            android:padding="12dp"
            android:layout_marginEnd="8dp" />

        <Button
            android:id="@+id/btnViewSchedule"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="View Schedule"
            android:textColor="#FFFFFF"
            android:backgroundTint="#388E3C"
            android:padding="12dp"
            android:layout_marginEnd="8dp" />

        <Button
            android:id="@+id/btnCheckStatus"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Check Status"
            android:textColor="#FFFFFF"
            android:backgroundTint="#D32F2F"
            android:padding="12dp" />

    </LinearLayout>

</LinearLayout>


FragmentTwo.kt
import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import androidx.fragment.app.Fragment
class FragmentTwo : Fragment() {
    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        return inflater.inflate(R.layout.fragment_two, container, false)
    }
}

fragment_two.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFFFFF"
    android:padding="16dp">

    <!-- Header Section -->
    <TextView
        android:id="@+id/headerTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:background="#3949AB"
        android:gravity="center"
        android:padding="16dp"
        android:text="My Trips"
        android:textColor="#FFFFFF"
        android:textSize="28sp"
        android:textStyle="bold" />

    <!-- Trip Details Section -->
    <ScrollView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <!-- Trip 1 -->
            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:background="#E3F2FD"
                android:padding="16dp"
                android:layout_marginBottom="8dp">

                <TextView
                    android:id="@+id/tripRoute1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Trip: Coimbatore (CBE) to Palakkad (PKD)"
                    android:textColor="#1E88E5"
                    android:textSize="18sp"
                    android:textStyle="bold" />

                <TextView
                    android:id="@+id/tripDate1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Date: 2024-11-10"
                    android:textColor="#555555"
                    android:textSize="16sp"
                    android:layout_marginTop="4dp" />

                <TextView
                    android:id="@+id/tripTime1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Time: 09:00 AM"
                    android:textColor="#555555"
                    android:textSize="16sp"
                    android:layout_marginTop="2dp" />

                <TextView
                    android:id="@+id/tripStatus1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Status: Confirmed"
                    android:textColor="#4CAF50"
                    android:textSize="16sp"
                    android:layout_marginTop="2dp" />
            </LinearLayout>

            <!-- Trip 2 -->
            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:background="#E3F2FD"
                android:padding="16dp"
                android:layout_marginBottom="8dp">

                <TextView
                    android:id="@+id/tripRoute2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Trip: Coimbatore (CBE) to Thrissur (TCR)"
                    android:textColor="#1E88E5"
                    android:textSize="18sp"
                    android:textStyle="bold" />

                <TextView
                    android:id="@+id/tripDate2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Date: 2024-11-15"
                    android:textColor="#555555"
                    android:textSize="16sp"
                    android:layout_marginTop="4dp" />

                <TextView
                    android:id="@+id/tripTime2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Time: 02:00 PM"
                    android:textColor="#555555"
                    android:textSize="16sp"
                    android:layout_marginTop="2dp" />

                <TextView
                    android:id="@+id/tripStatus2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Status: Cancelled"
                    android:textColor="#D32F2F"
                    android:textSize="16sp"
                    android:layout_marginTop="2dp" />
            </LinearLayout>

            <!-- Additional trips can follow the same layout -->

        </LinearLayout>
    </ScrollView>

</LinearLayout>


FragmentThree.kt

import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import androidx.fragment.app.Fragment
import com.example.exp10.R

class FragmentThree : Fragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?,
                              savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.fragment_three, container, false)
    }
}

fragment_three.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFFFFF"
    android:padding="16dp">

    <!-- Header Section -->
    <TextView
        android:id="@+id/headerTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:background="#D81B60"
        android:gravity="center"
        android:padding="16dp"
        android:text="Payment Details"
        android:textColor="#FDFCFC"
        android:textSize="28sp"
        android:textStyle="bold" />

    <!-- Payment Method Section -->
    <TextView
        android:id="@+id/paymentMethodsTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Saved Payment Methods"
        android:textColor="#000000"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginTop="16dp" />

    <!-- Credit Card -->
    <TextView
        android:id="@+id/creditCard"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Credit Card: **** **** **** 2412"
        android:textColor="#333333"
        android:textSize="16sp"
        android:padding="12dp"
        android:background="#E0E0E0"
        android:layout_marginTop="8dp" />

    <!-- Debit Card -->
    <TextView
        android:id="@+id/debitCard"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Debit Card: **** **** **** 1235"
        android:textColor="#333333"
        android:textSize="16sp"
        android:padding="12dp"
        android:background="#E0E0E0"
        android:layout_marginTop="4dp" />

    <!-- Cash Option -->
    <TextView
        android:id="@+id/cashOption"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Cash"
        android:textColor="#333333"
        android:textSize="16sp"
        android:padding="12dp"
        android:background="#E0E0E0"
        android:layout_marginTop="4dp" />

    <!-- Action Buttons Section -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="24dp">

        <Button
            android:id="@+id/btnAddPaymentMethod"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Add New Payment Method"
            android:textColor="#FFFFFF"
            android:backgroundTint="#1976D2"
            android:padding="12dp"
            android:layout_marginEnd="8dp" />

        <Button
            android:id="@+id/btnManagePaymentMethods"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Manage"
            android:textColor="#FFFFFF"
            android:backgroundTint="#388E3C"
            android:padding="12dp" />

    </LinearLayout>

</LinearLayout>

build.gradle(app)


dependencies {
    implementation("androidx.core:core-ktx:1.12.0") // Switch to 1.12.0
    implementation(libs.androidx.appcompat)
    implementation(libs.material)
    implementation(libs.androidx.activity)
    implementation(libs.androidx.constraintlayout)

    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)

    implementation("com.google.android.material:material:1.11.0")
    implementation("androidx.viewpager2:viewpager2:1.1.0-beta01")
    implementation("androidx.fragment:fragment-ktx:1.6.1")
}

ViewPagerAdapter.kt

import FragmentThree
import androidx.appcompat.app.AppCompatActivity
import androidx.fragment.app.Fragment
import androidx.viewpager2.adapter.FragmentStateAdapter
class ViewPagerAdapter(activity: AppCompatActivity) : FragmentStateAdapter(activity) {
    override fun getItemCount(): Int = 3 // Number of tabs

    override fun createFragment(position: Int): Fragment {
        return when (position) {
            0 -> FragmentOne() // Ensure ChatsFragment is a valid Fragment class
            1 -> FragmentTwo() // Assuming StatusFragment is properly defined
            2 -> FragmentThree() // Assuming CallsFragment is properly defined
            else -> throw IllegalArgumentException("Invalid position")
        }
    }
}




