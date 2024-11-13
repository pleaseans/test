01 - BMI calculator
https://drive.google.com/file/d/1QZ0YqwZrVU1uJW9TF2XfJsXfAsIFQWZF/view?usp=drive_link
MainActivity.kt
package com.example.myapplication
import android.os.Bundle
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import androidx.lifecycle.findViewTreeViewModelStoreOwner
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        var text1:EditText =findViewById(R.id.text1)
        var text2two:EditText = findViewById(R.id.text2two)
        var button1:Button = findViewById(R.id.button1)
        var result: TextView = findViewById(R.id.result)
        var res: TextView = findViewById(R.id.textView4)

        //Event handing Code
        button1.setOnClickListener{
            var weight:Float = text1.text.toString().toFloat()
            var height:Float = (text2two.text.toString().toFloat())/100
            val bmi: Float = weight / (height * height)
            result.text = "%.2f".format(bmi)
            if (bmi<18){
                res.text="Underweight"
            }
            else if (bmi>=18 && bmi<25){
                res.text="Normal"
            }
            else if (bmi>=25 && bmi<30){
                res.text="Overweight"
            }
            else if (bmi>=30){
                res.text="Obese"
            }
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

    <EditText
        android:id="@+id/text1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="32dp"
        android:ems="10"
        android:fontFamily="sans-serif-medium"
        android:hint="ENTER THE WEIGHT"
        android:inputType="text"
        android:textColor="#5F166B"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="@+id/textView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/no2box"
        android:layout_width="78dp"
        android:layout_height="39dp"
        android:layout_marginStart="32dp"
        android:fontFamily="sans-serif-medium"
        android:text="HEIGHT"
        android:textColorHighlight="#100C0C"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="@+id/text2two"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        app:layout_constraintVertical_bias="1.0" />

    <EditText
        android:id="@+id/text2two"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="36dp"
        android:layout_marginEnd="60dp"
        android:ems="10"
        android:fontFamily="sans-serif-medium"
        android:hint="ENTER THE HEIGHT"
        android:inputType="text"
        android:textColor="#5F166B"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text1" />

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="64dp"
        android:fontFamily="sans-serif-medium"
        android:text="CALCULATE"
        android:textSize="20sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.394"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text2two" />

    <TextView
        android:id="@+id/result"
        android:layout_width="166dp"
        android:layout_height="77dp"
        android:layout_marginTop="80dp"
        android:layout_marginEnd="32dp"
        android:fontFamily="sans-serif-medium"
        android:textSize="20sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button1" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="76dp"
        android:layout_height="33dp"
        android:layout_marginStart="32dp"
        android:layout_marginTop="44dp"
        android:fontFamily="sans-serif-medium"
        android:text="WEIGHT"
        android:textColorHighlight="#020101"
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="336dp"
        android:layout_height="75dp"
        android:layout_marginTop="60dp"
        android:fontFamily="sans-serif-black"
        android:text="BMI CALCULATOR"
        android:textColor="#591A64"
        android:textColorLink="#7F2A8E"
        android:textSize="34sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.75"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="113dp"
        android:layout_height="61dp"
        android:layout_marginTop="12dp"
        android:fontFamily="sans-serif-medium"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.714"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/result" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="112dp"
        android:layout_height="50dp"
        android:layout_marginStart="56dp"
        android:layout_marginBottom="24dp"
        android:fontFamily="sans-serif-medium"
        android:text="BMI SCORE"
        android:textColorHighlight="#000000"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="@+id/result"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/textView5"
        android:layout_width="114dp"
        android:layout_height="39dp"
        android:layout_marginStart="56dp"
        android:layout_marginBottom="20dp"
        android:fontFamily="sans-serif-medium"
        android:text="BODY TYPE"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="@+id/textView4"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>

02 - intent
https://drive.google.com/file/d/1ZAbQKTQiKYMo23IkF49uLMy7c3xxkfBC/view?usp=sharing
MainActivity.kt
package com.example.myapplication_intent
import androidx.activity.enableEdgeToEdge
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
import android.content.Intent
import android.os.Bundle
import android.widget.*
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)

        val name: EditText = findViewById(R.id.editTextText2)
        val dateofv: EditText = findViewById(R.id.editTextText41)
        val radioGroup: RadioGroup = findViewById(R.id.radioGroup)
        val spinner: Spinner = findViewById(R.id.spinner)
        val items = arrayOf("Cardiology", "Neurology", "Pediatrician","Dermatologist","Dentist","ENT","Others")
        val arrayAdapter: ArrayAdapter<String> = ArrayAdapter(
            this, android.R.layout.simple_spinner_item, items
        )
       arrayAdapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        spinner.adapter = arrayAdapter
        val ch1: CheckBox = findViewById(R.id.checkBox61)
        val ch2: CheckBox = findViewById(R.id.checkBox62)
        val ch3: CheckBox = findViewById(R.id.checkBox63)
        val ch4: CheckBox = findViewById(R.id.checkBox64)
        val switch: Switch = findViewById(R.id.switch1)
        val btn: Button = findViewById(R.id.button)
        btn.setOnClickListener {
            val intent = Intent(this, second_activity::class.java).apply {
                putExtra("name", name.text.toString())
                putExtra("dateofv", dateofv.text.toString())
                // Get selected radio button ID and the corresponding value
                val selectedRadioButtonId = radioGroup.checkedRadioButtonId
                val selectedRadioButtonText = if (selectedRadioButtonId != -1) {
                    findViewById<RadioButton>(selectedRadioButtonId).text.toString()
                } else {
                    ""
                }
                putExtra("radioGroup", selectedRadioButtonText)

                // Get spinner selection
                putExtra("spinner", spinner.selectedItem.toString())

                // Get checkbox states
                putExtra("ch1", ch1.isChecked)
                putExtra("ch2", ch2.isChecked)
                putExtra("ch3", ch3.isChecked)
                putExtra("ch4", ch4.isChecked)
                putExtra("switchAdmission", switch.isChecked)

            }

            // Start the Activity
            startActivity(intent)
        }
    }
}
Second_activity.kt
package com.example.myapplication_intent

import android.os.Bundle
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class second_activity:AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.secondactivity)

        // Retrieve data from the Intent
        val name = intent.getStringExtra("name")
        val dateOfVisit = intent.getStringExtra("dateofv")
        val gender = intent.getStringExtra("radioGroup")
        val department = intent.getStringExtra("spinner")

        val ch1Checked = intent.getBooleanExtra("ch1", false)
        val ch2Checked = intent.getBooleanExtra("ch2", false)
        val ch3Checked = intent.getBooleanExtra("ch3", false)
        val ch4Checked = intent.getBooleanExtra("ch4", false)

        val symptoms = mutableListOf<String>()
        if (ch1Checked) symptoms.add("Fever")
        if (ch2Checked) symptoms.add("Vomiting")
        if (ch3Checked) symptoms.add("Cough")
        if (ch4Checked) symptoms.add("Pain")

        // Admission willingness
        val admission = if (intent.getBooleanExtra("switch1", false)) "No" else "Yes"

        // Set the data to TextViews in the TableLayout
        findViewById<TextView>(R.id.textViewName).text = name
        findViewById<TextView>(R.id.textViewGender).text = gender
        findViewById<TextView>(R.id.textViewDateOfVisit).text = dateOfVisit
        findViewById<TextView>(R.id.textViewDepartment).text = department
        findViewById<TextView>(R.id.textViewSymptoms).text = symptoms.joinToString(", ")
        findViewById<TextView>(R.id.textViewAdmission).text = admission
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
        android:id="@+id/textView1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="33dp"
        android:layout_marginBottom="34dp"
        android:text="HOSPITAL OUTPATIENT VISIT"
        android:textSize="20sp"
        app:layout_constraintBottom_toTopOf="@+id/imageView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginEnd="11dp"
        android:layout_marginBottom="70dp"
        android:text="Name of the patient"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextText41"
        app:layout_constraintEnd_toStartOf="@+id/editTextText2"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/editTextText2"
        android:layout_width="0dp"
        android:layout_height="39dp"
        android:layout_marginEnd="45dp"
        android:ems="10"
        android:hint="Enter the name"
        android:inputType="text"
        android:textSize="16sp"
        app:layout_constraintBaseline_toBaselineOf="@+id/textView2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView2" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginEnd="22dp"
        android:text="Gender"
        android:textSize="16sp"
        app:layout_constraintEnd_toStartOf="@+id/radioGroup"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="@+id/radioGroup" />

    <RadioGroup
        android:id="@+id/radioGroup"
        android:layout_width="0dp"
        android:layout_height="29dp"
        android:layout_marginTop="19dp"
        android:layout_marginEnd="65dp"
        android:layout_marginBottom="18dp"
        android:orientation="horizontal"
        app:layout_constraintBottom_toTopOf="@+id/editTextText41"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView3"
        app:layout_constraintTop_toBottomOf="@+id/editTextText2">

        <RadioButton
            android:id="@+id/radioButton31"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Male" />

        <RadioButton
            android:id="@+id/radioButton32"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Female" />
    </RadioGroup>

    <TextView
        android:id="@+id/textView4"
        android:layout_width="84dp"
        android:layout_height="68dp"
        android:layout_marginEnd="20dp"
        android:text="Date of Visit"
        android:textSize="16sp"
        app:layout_constraintBaseline_toBaselineOf="@+id/editTextText41"
        app:layout_constraintEnd_toStartOf="@+id/editTextText41" />

    <EditText
        android:id="@+id/editTextText41"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="19dp"
        android:ems="10"
        android:hint="Enter the date of visit"
        android:inputType="text"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/textView5"
        app:layout_constraintEnd_toEndOf="@+id/textView5"
        app:layout_constraintStart_toEndOf="@+id/textView5" />

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="40dp"
        android:text="Department of appointment"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/checkBox62"
        app:layout_constraintStart_toStartOf="@+id/spinner" />

    <Spinner
        android:id="@+id/spinner"
        android:layout_width="0dp"
        android:layout_height="26dp"
        android:layout_marginStart="41dp"
        android:layout_marginTop="110dp"
        android:layout_marginEnd="37dp"
        android:layout_marginBottom="110dp"
        app:layout_constraintBottom_toTopOf="@+id/textView7"
        app:layout_constraintEnd_toEndOf="@+id/checkBox63"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/radioGroup" />

    <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="15dp"
        android:layout_marginEnd="10dp"
        android:text="Symptoms"
        android:textSize="16sp"
        app:layout_constraintBaseline_toBaselineOf="@+id/checkBox61"
        app:layout_constraintEnd_toStartOf="@+id/checkBox61"
        app:layout_constraintHorizontal_chainStyle="packed"
        app:layout_constraintStart_toStartOf="parent" />

    <CheckBox
        android:id="@+id/checkBox61"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="5dp"
        android:layout_marginBottom="3dp"
        android:text="Fever"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/checkBox64"
        app:layout_constraintEnd_toStartOf="@+id/checkBox62"
        app:layout_constraintStart_toEndOf="@+id/textView6" />

    <CheckBox
        android:id="@+id/checkBox62"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="3dp"
        android:text="Vomiting"
        android:textSize="16sp"
        app:layout_constraintBaseline_toBaselineOf="@+id/checkBox63"
        app:layout_constraintEnd_toStartOf="@+id/checkBox63"
        app:layout_constraintStart_toEndOf="@+id/checkBox61" />

    <CheckBox
        android:id="@+id/checkBox63"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="53dp"
        android:text="Cough"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/switch1"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/checkBox62" />

    <CheckBox
        android:id="@+id/checkBox64"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="9dp"
        android:layout_marginBottom="4dp"
        android:text="Pain"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/textView7"
        app:layout_constraintEnd_toEndOf="@+id/checkBox61" />

    <TextView
        android:id="@+id/textView7"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="4dp"
        android:layout_marginEnd="5dp"
        android:layout_marginBottom="100dp"
        android:text="Willing to be admitted"
        android:textSize="16sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/checkBox62"
        app:layout_constraintStart_toStartOf="@+id/textView6" />

    <Switch
        android:id="@+id/switch1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="21dp"
        android:layout_marginBottom="3dp"
        android:text="Yes"
        android:textSize="16sp"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintStart_toEndOf="@+id/textView7" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="6dp"
        android:layout_marginEnd="39dp"
        android:text="Submit"
        app:layout_constraintEnd_toEndOf="@+id/switch1"
        app:layout_constraintTop_toBottomOf="@+id/textView7" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="160dp"
        android:layout_height="0dp"
        android:layout_marginBottom="462dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView1"
        app:srcCompat="@drawable/istockphoto_1344779917_612x612" />

</androidx.constraintlayout.widget.ConstraintLayout>

secondactivity.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".secondactivity">

    <TableLayout
        android:id="@+id/tableLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:stretchColumns="1"
        android:layout_margin="16dp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toBottomOf="parent">

        <!-- Name Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Name"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewName"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

        <!-- Gender Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Gender"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewGender"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

        <!-- Date of Visit Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Date of Visit"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewDateOfVisit"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

        <!-- Department Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Department"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewDepartment"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

        <!-- Symptoms Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Symptoms"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewSymptoms"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

        <!-- Admission Willingness Row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Willing to be Admitted"
                android:textStyle="bold"
                android:padding="8dp" />

            <TextView
                android:id="@+id/textViewAdmission"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:padding="8dp" />
        </TableRow>

    </TableLayout>
</androidx.constraintlayout.widget.ConstraintLayout>

##androidmanifest.xml
 <activity
            android:name=".second_activity"
            android:exported="false" />

03 - Database
https://drive.google.com/file/d/1G-jhm7lu41fDxnIdUmLoFAqBek7E16F6/view?usp=sharing
MainActivity.kt
package com.example.databaseexample

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.util.Log

class MainActivity : AppCompatActivity() {

    private lateinit var dbHelper: MyDatabaseHelper
    private lateinit var editTextName: EditText
    private lateinit var editTextAge: EditText
    private lateinit var textViewUsers: TextView
    private lateinit var editTextUserId: EditText
    private lateinit var buttonAddUser: Button
    private lateinit var buttonViewUsers: Button
    private lateinit var buttonUpdateUser: Button
    private lateinit var buttonDeleteUser: Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        dbHelper = MyDatabaseHelper(this)

        // Bind UI elements to variables
        editTextName = findViewById(R.id.editTextName)
        editTextAge = findViewById(R.id.editTextAge)
        editTextUserId = findViewById(R.id.editTextUserId)
        textViewUsers = findViewById(R.id.textViewUsers)
        buttonAddUser = findViewById(R.id.buttonAddUser)
        buttonViewUsers = findViewById(R.id.buttonViewUsers)
        buttonUpdateUser = findViewById(R.id.buttonUpdateUser)
        buttonDeleteUser = findViewById(R.id.buttonDeleteUser)

        // Add User
        buttonAddUser.setOnClickListener {
            val name = editTextName.text.toString()
            val age = editTextAge.text.toString().toIntOrNull()

            if (name.isNotBlank() && age != null) {
                dbHelper.insertUser(name, age)
                Log.d("AddUser", "User added: Name: $name, Age: $age")
            } else {
                Log.d("AddUser", "Failed to add user: Invalid name or age.")
            }
        }

        // View Users
        buttonViewUsers.setOnClickListener {
            val users = dbHelper.getAllUsers()
            if (users.isNotEmpty()) {
                val userString = users.joinToString(separator = "\n") { "ID: ${it.id}, Name: ${it.name}, Age: ${it.age}" }
                textViewUsers.text = userString
                Log.d("ViewUsers", "Users found: $userString")
            } else {
                textViewUsers.text = "No users found."
                Log.d("ViewUsers", "No users found in the database.")
            }
        }

        // Update User
        buttonUpdateUser.setOnClickListener {
            val userId = editTextUserId.text.toString().toIntOrNull()
            val name = editTextName.text.toString()
            val age = editTextAge.text.toString().toIntOrNull()

            if (userId != null && name.isNotBlank() && age != null) {
                val rowsUpdated = dbHelper.updateUser(userId, name, age)
                if (rowsUpdated > 0) {
                    Log.d("UpdateUser", "User updated: ID: $userId, Name: $name, Age: $age")
                } else {
                    Log.d("UpdateUser", "Failed to update user: ID not found.")
                }
            } else {
                Log.d("UpdateUser", "Invalid input: Enter a valid ID, name, and age.")
            }
        }

        // Delete User
        buttonDeleteUser.setOnClickListener {
            val userId = editTextUserId.text.toString().toIntOrNull()

            if (userId != null) {
                val rowsDeleted = dbHelper.deleteUser(userId)
                if (rowsDeleted > 0) {
                    Log.d("DeleteUser", "User deleted: ID: $userId")
                } else {
                    Log.d("DeleteUser", "Failed to delete user: ID not found.")
                }
            } else {
                Log.d("DeleteUser", "Invalid input: Enter a valid ID.")
            }
        }
    }
}

MyDatabaseHelper.kt
package com.example.databaseexample

import android.content.Context
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper
import android.content.ContentValues

class MyDatabaseHelper(context: Context) : SQLiteOpenHelper(context, DATABASE_NAME, null, DATABASE_VERSION) {

    companion object {
        const val DATABASE_NAME = "mydatabase.db"
        const val DATABASE_VERSION = 1
        const val TABLE_NAME = "Users"
        const val COLUMN_ID = "id"
        const val COLUMN_NAME = "name"
        const val COLUMN_AGE = "age"
    }

    override fun onCreate(db: SQLiteDatabase) {
        val createTable = ("CREATE TABLE $TABLE_NAME (" +
                "$COLUMN_ID INTEGER PRIMARY KEY AUTOINCREMENT, " +
                "$COLUMN_NAME TEXT, " +
                "$COLUMN_AGE INTEGER)")
        db.execSQL(createTable)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS $TABLE_NAME")
        onCreate(db)
    }

    // Insert Operation
    fun insertUser(name: String, age: Int) {
        val db = this.writableDatabase
        val values = ContentValues().apply {
            put(COLUMN_NAME, name)
            put(COLUMN_AGE, age)
        }
        db.insert(TABLE_NAME, null, values)
        db.close()
    }

    // Read Operation
    fun getAllUsers(): List<User> {
        val userList = mutableListOf<User>()
        val db = this.readableDatabase
        val cursor = db.rawQuery("SELECT * FROM $TABLE_NAME", null)

        if (cursor.moveToFirst()) {
            do {
                val user = User(
                    id = cursor.getInt(cursor.getColumnIndexOrThrow(COLUMN_ID)),
                    name = cursor.getString(cursor.getColumnIndexOrThrow(COLUMN_NAME)),
                    age = cursor.getInt(cursor.getColumnIndexOrThrow(COLUMN_AGE))
                )
                userList.add(user)
            } while (cursor.moveToNext())
        }

        cursor.close()
        db.close()
        return userList
    }

    // Update Operation
    fun updateUser(id: Int, name: String, age: Int): Int {
        val db = this.writableDatabase
        val values = ContentValues().apply {
            put(COLUMN_NAME, name)
            put(COLUMN_AGE, age)
        }
        val success = db.update(TABLE_NAME, values, "$COLUMN_ID=?", arrayOf(id.toString()))
        db.close()
        return success
    }

    // Delete Operation
    fun deleteUser(id: Int): Int {
        val db = this.writableDatabase
        val success = db.delete(TABLE_NAME, "$COLUMN_ID=?", arrayOf(id.toString()))
        db.close()
        return success
    }
}
user.kt
package com.example.databaseexample

data class User(
    val id: Int,
    val name: String,
    val age: Int
)
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/textViewTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="User Database"
        android:textSize="24sp"
        android:textStyle="bold"
        android:layout_gravity="center"
        android:paddingBottom="16dp" />

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Name" />

    <EditText
        android:id="@+id/editTextAge"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Age"
        android:inputType="number" />

    <EditText
        android:id="@+id/editTextUserId"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter User ID for Update/Delete"
        android:inputType="number"
        android:layout_marginTop="8dp" />

    <Button
        android:id="@+id/buttonAddUser"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Add User"
        android:layout_marginTop="16dp" />

    <Button
        android:id="@+id/buttonUpdateUser"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Update User"
        android:layout_marginTop="8dp" />

    <Button
        android:id="@+id/buttonDeleteUser"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Delete User"
        android:layout_marginTop="8dp" />

    <Button
        android:id="@+id/buttonViewUsers"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="View Users"
        android:layout_marginTop="8dp" />

    <TextView
        android:id="@+id/textViewUsers"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Users will be shown here"
        android:paddingTop="16dp"
        android:textSize="16sp"
        android:layout_marginTop="8dp" />
</LinearLayout>

04 - Listview
https://drive.google.com/file/d/1XcBpe6KCJu7EbbLsEdPZa750ssuxlBTq/view?usp=sharing
MainActivity.kt
package com.example.listview
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

        val mylistview: ListView = findViewById(R.id.list_view)

        // Create a list of persons
        val persons = listOf(
            Person("101", 50, "52", R.drawable.f1),
            Person("202", 60, "60", R.drawable.f2),
            Person("303", 45, "100", R.drawable.f3),
            Person("404", 55, "123", R.drawable.f44),
            Person("505", 40, "90", R.drawable.f5),

            )

        // Set the custom adapter
        val adapter = PersonAdapter(this, R.layout.list_item, persons)
        mylistview.adapter = adapter

        // Handle item click
        mylistview.setOnItemClickListener { parent, view, position, id ->
            val selectedPerson = persons[position]
            Toast.makeText(this, "Item ID: ${selectedPerson.name}, price: ${selectedPerson.age}, qty: ${selectedPerson.gender}",
                Toast.LENGTH_LONG
            ).show()
        }
    }
}
PersonAdapter.kt
package com.example.listview

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
        val nameTextView: TextView = view.findViewById(R.id.busname)
        val ageTextView: TextView = view.findViewById(R.id.buscapacity)
        val genderTextView: TextView = view.findViewById(R.id.busroute)
        val busImage = view.findViewById<ImageView>(R.id.busimage)


        // Set data to the TextViews
        nameTextView.text = person.name
        ageTextView.text = "price: ${person.age}"
        genderTextView.text = "qty: ${person.gender}"
        busImage.setImageResource(person.imageResId)
        return view
        }
}

Person.kt
package com.example.listview

data class Person(val name: String, val age: Int, val gender: String,val imageResId:Int)

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">


    <ListView
        android:id="@+id/list_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</LinearLayout>

list_item.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">


    <ListView
        android:id="@+id/list_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</LinearLayout>

05- content providers phone call
https://drive.google.com/file/d/1v8gNqFG1GWLr3Rg7ax9a-hfZQ-JDiaxU/view?usp=sharing
MainActivity.kt
package com.example.ex_5

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
                cursor.close()
            }

            val adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, contactList)
            listView.adapter = adapter

            // Set an item click listener to make a call when a contact is selected
            listView.setOnItemClickListener { _, _, position, _ ->
                val selectedNumber = contactNumbers[position]
                makeCall(selectedNumber)
            }
        }
    }

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
            Toast.makeText(this, "Unable to make the call", Toast.LENGTH_SHORT).show()
        }
    }
}

activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_marginTop="30dp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Content Provider Example"
        android:layout_gravity="center_horizontal"
        android:textColor="#D81B60" />

    <Button
        android:id="@+id/loadbtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Load Contacts"
        android:layout_marginTop="20dp" />

    <ListView
        android:id="@+id/listView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp" />
</LinearLayout>

##androidManifest.xml
<uses-permission android:name="android.permission.READ_CONTACTS"/>
    <uses-permission android:name="android.permission.CALL_PHONE"/>

06 - broadcast battery level
https://drive.google.com/file/d/1KDV0NYKqseBtewtfCBLEA9cqd-VXjC9m/view?usp=sharing
MainActivity.kt
package com.example.ex_6

import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.content.IntentFilter
import android.os.BatteryManager
import android.os.Bundle
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    private lateinit var batteryReceiver: BroadcastReceiver
    private lateinit var batteryLevelTextView: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Find the TextView in the layout to display the battery level
        batteryLevelTextView = findViewById(R.id.batteryLevelTextView)

        // Register the broadcast receiver for battery changes
        val intentFilter = IntentFilter(Intent.ACTION_BATTERY_CHANGED)
        batteryReceiver = BatteryLevelReceiver()
        registerReceiver(batteryReceiver, intentFilter)
    }

    override fun onDestroy() {
        super.onDestroy()
        unregisterReceiver(batteryReceiver)
    }

    class BatteryLevelReceiver : BroadcastReceiver() {
        override fun onReceive(context: Context?, intent: Intent?) {
            if (intent?.action == Intent.ACTION_BATTERY_CHANGED) {
                val level = intent.getIntExtra(BatteryManager.EXTRA_LEVEL, -1)
                val scale = intent.getIntExtra(BatteryManager.EXTRA_SCALE, -1)
                val batteryPct = level * 100 / scale


                val mainActivity = context as MainActivity
                mainActivity.batteryLevelTextView.text = "Battery Level: $batteryPct%"

                // Show a toast message if the battery level is below 20%
                if (batteryPct < 20) {
                    Toast.makeText(context, "Battery low: $batteryPct%", Toast.LENGTH_LONG).show()
                }
            }
        }
    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#E0BBE4"
    tools:context=".MainActivity">

    <!-- TextView to display the current battery level -->
    <TextView
        android:id="@+id/batteryLevelTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Battery Level: "
        android:textSize="20sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toBottomOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

07 - Media player
https://drive.google.com/file/d/1mZBVu_x7clQD3ocNSknhW4I_xaZgoJR_/view?usp=sharing
MainActivity.kt
package com.example.ex_7

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

package com.example.ex_7

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

08 - user sms
https://drive.google.com/file/d/14kZV0pUqpPLH2JQUZGgU82U_SSVB0vo-/view?usp=sharing
MainActivity.kt

package com.example.userpassshared_sms
import android.content.Intent
import android.content.SharedPreferences
import android.os.Bundle
import android.telephony.SmsManager
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat

class MainActivity : AppCompatActivity() {

    private lateinit var sharedPreferences: SharedPreferences

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        sharedPreferences = getSharedPreferences("LoginPrefs", MODE_PRIVATE)

        // Sample data to simulate stored credentials
        saveSampleCredentials("user1", "pass1")

        // Request SMS permission at runtime
        ActivityCompat.requestPermissions(this, arrayOf(android.Manifest.permission.SEND_SMS), 1)

        val usernameField: EditText = findViewById(R.id.username)
        val passwordField: EditText = findViewById(R.id.password)
        val loginButton: Button = findViewById(R.id.loginButton)

        loginButton.setOnClickListener {
            val username = usernameField.text.toString()
            val password = passwordField.text.toString()

            if (checkCredentials(username, password)) {
                sendSms("Login Successful")
                Toast.makeText(this, "Login Successful", Toast.LENGTH_SHORT).show()
            } else {
                sendSms("Login Failed")
                Toast.makeText(this, "Login Failed", Toast.LENGTH_SHORT).show()
            }
        }
    }

    private fun saveSampleCredentials(username: String, password: String) {
        val editor = sharedPreferences.edit()
        editor.putString("Username", username)
        editor.putString("Password", password)
        editor.apply()
    }

    private fun checkCredentials(username: String, password: String): Boolean {
        val storedUsername = sharedPreferences.getString("Username", "")
        val storedPassword = sharedPreferences.getString("Password", "")
        return (username == storedUsername && password == storedPassword)
    }

    private fun sendSms(message: String) {
        try {
            val smsManager: SmsManager = SmsManager.getDefault()
            val phoneNumber = "1234567890" // Replace with a valid phone number
            smsManager.sendTextMessage(phoneNumber, null, message, null, null)
        } catch (e: Exception) {
            e.printStackTrace()
            Toast.makeText(this, "SMS Failed to Send", Toast.LENGTH_SHORT).show()
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
        android:id="@+id/username"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Username"/>

    <EditText
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password"
        android:inputType="textPassword"/>

    <Button
        android:id="@+id/loginButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Login"
        android:layout_gravity="center_horizontal"/>
</LinearLayout>

##AndroidManifest.xml
<uses-feature android:name="android.hardware.telephony"></uses-feature>
    <uses-permission android:name="android.permission.SEND_SMS"/>

09 - user email time
https://drive.google.com/file/d/1Q1tJ2LJNLLc6VNWPxY6FNHaZ1nJWM_9C/view?usp=sharing
MainActivity.kt
package com.example.userpass_email

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import java.text.SimpleDateFormat
import java.util.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val usernameField: EditText = findViewById(R.id.usernameField)
        val passwordField: EditText = findViewById(R.id.passwordField)
        val loginButton: Button = findViewById(R.id.loginButton)

        loginButton.setOnClickListener {
            val username = usernameField.text.toString()
            val password = passwordField.text.toString()

            if (username.isNotEmpty() && password.isNotEmpty()) {
                sendLoginEmail(username)
            } else {
                Toast.makeText(this, "Please enter both Username and Password", Toast.LENGTH_SHORT).show()
            }
        }
    }
    private fun sendLoginEmail(username: String) {
        val email = "your_email@example.com" // Replace with your email address
        val subject = "Login Entry"
        val dateTime = getCurrentDateTime()
        val message = "Username: $username\nDate and Time of Login: $dateTime"

        val emailIntent = Intent(Intent.ACTION_SEND).apply {
            type = "message/rfc822"
            putExtra(Intent.EXTRA_EMAIL, arrayOf(email))
            putExtra(Intent.EXTRA_SUBJECT, subject)
            putExtra(Intent.EXTRA_TEXT, message)
        }
        try {
            startActivity(Intent.createChooser(emailIntent, "Send email using..."))
        } catch (ex: Exception) {
            Toast.makeText(this, "No email clients installed.", Toast.LENGTH_SHORT).show()
        }
    }

    private fun getCurrentDateTime(): String {
        val dateFormat = SimpleDateFormat("yyyy-MM-dd HH:mm:ss", Locale.getDefault())
        return dateFormat.format(Date())
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

    <EditText
        android:id="@+id/usernameField"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Username" />

    <EditText
        android:id="@+id/passwordField"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Password"
        android:inputType="textPassword" />

    <Button
        android:id="@+id/loginButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Login"
        android:layout_gravity="center_horizontal" />
</LinearLayout>

##AndroidManifest.xml
<uses-permission android:name="android.permission.INTERNET"></uses-permission>

10 - Room database
https://drive.google.com/file/d/1QqOBeanS_yJui_P8XFgP4__3elYoCI0T/view?usp=sharing
MainActivity.kt

package com.example.roomdb
import android.database.Cursor
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private lateinit var dbHelper: MyDatabaseHelper

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        dbHelper = MyDatabaseHelper(this)

        val bookNameField: EditText = findViewById(R.id.bookName)
        val authorNameField: EditText = findViewById(R.id.authorName)
        val bookPriceField: EditText = findViewById(R.id.bookPrice)
        val saveButton: Button = findViewById(R.id.saveButton)
        val searchBookNameField: EditText = findViewById(R.id.searchBookName)
        val searchButton: Button = findViewById(R.id.searchButton)

        saveButton.setOnClickListener {
            val bookName = bookNameField.text.toString()
            val author = authorNameField.text.toString()
            val price = bookPriceField.text.toString().toDouble()

            if (bookName.isNotEmpty() && author.isNotEmpty()) {
                dbHelper.addBook(bookName, author, price)
                Toast.makeText(this, "Book Saved Successfully", Toast.LENGTH_SHORT).show()

            } else {
                Toast.makeText(this, "Please fill in all fields", Toast.LENGTH_SHORT).show()
            }
        }

        searchButton.setOnClickListener {
            val searchBookName = searchBookNameField.text.toString()

            dbHelper.searchBook(searchBookName)?.use { cursor ->
                if (cursor.moveToFirst()) {
                    val bookName = cursor.getString(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_BOOK_NAME))
                    val author = cursor.getString(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_AUTHOR_NAME))
                    val price = cursor.getDouble(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_BOOK_PRICE))

                    Toast.makeText(this, "Book Found:Name: $bookName Author: $author Price: $price", Toast.LENGTH_LONG).show()
                } else {
                    Toast.makeText(this, "Book Not Found", Toast.LENGTH_SHORT).show()
                }
            }
        }

    }
}

MyDatabaseHelper.kt

package com.example.roomdb
import android.database.Cursor
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private lateinit var dbHelper: MyDatabaseHelper

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        dbHelper = MyDatabaseHelper(this)

        val bookNameField: EditText = findViewById(R.id.bookName)
        val authorNameField: EditText = findViewById(R.id.authorName)
        val bookPriceField: EditText = findViewById(R.id.bookPrice)
        val saveButton: Button = findViewById(R.id.saveButton)
        val searchBookNameField: EditText = findViewById(R.id.searchBookName)
        val searchButton: Button = findViewById(R.id.searchButton)

        saveButton.setOnClickListener {
            val bookName = bookNameField.text.toString()
            val author = authorNameField.text.toString()
            val price = bookPriceField.text.toString().toDouble()

            if (bookName.isNotEmpty() && author.isNotEmpty()) {
                dbHelper.addBook(bookName, author, price)
                Toast.makeText(this, "Book Saved Successfully", Toast.LENGTH_SHORT).show()

            } else {
                Toast.makeText(this, "Please fill in all fields", Toast.LENGTH_SHORT).show()
            }
        }

        searchButton.setOnClickListener {
            val searchBookName = searchBookNameField.text.toString()

            dbHelper.searchBook(searchBookName)?.use { cursor ->
                if (cursor.moveToFirst()) {
                    val bookName = cursor.getString(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_BOOK_NAME))
                    val author = cursor.getString(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_AUTHOR_NAME))
                    val price = cursor.getDouble(cursor.getColumnIndexOrThrow(MyDatabaseHelper.COLUMN_BOOK_PRICE))

                    Toast.makeText(this, "Book Found:Name: $bookName Author: $author Price: $price", Toast.LENGTH_LONG).show()
                } else {
                    Toast.makeText(this, "Book Not Found", Toast.LENGTH_SHORT).show()
                }
            }
        }

    }
}

Book.kt
package com.example.roomdb

class Book (
    val id: Int,
    val name:String,
    val author: String,
    val price: Double,
)

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/bookName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Book Name" />

    <EditText
        android:id="@+id/authorName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Author Name" />

    <EditText
        android:id="@+id/bookPrice"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Book Price"
        android:inputType="numberDecimal" />

    <Button
        android:id="@+id/saveButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Save Book"
        android:layout_gravity="center_horizontal" />

    <EditText
        android:id="@+id/searchBookName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Search Book Name" />

    <Button
        android:id="@+id/searchButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Search Book"
        android:layout_gravity="center_horizontal" />
</LinearLayout>


######

import requests
import re

def download_file_from_google_drive(link, destination):
    file_id = extract_file_id(link)
    base_url = "https://drive.google.com/uc?export=download"
    session = requests.Session()

    response = session.get(base_url, params={'id': file_id}, stream=True)
    token = get_confirm_token(response)

    if token:
        params = {'id': file_id, 'confirm': token}
        response = session.get(base_url, params=params, stream=True)

    save_response_content(response, destination)

def extract_file_id(link):
    match = re.search(r'/d/([\w-]+)', link)
    if match:
        return match.group(1)
    else:
        raise ValueError("Invalid link format")

def get_confirm_token(response):
    for key, value in response.cookies.items():
        if key.startswith('download_warning'):
            return value
    return None

def save_response_content(response, destination):
    CHUNK_SIZE = 32768

    with open(destination, 'wb') as f:
        for chunk in response.iter_content(CHUNK_SIZE):
            if chunk:  # filter out keep-alive new chunks
                f.write(chunk)

if _name_ == "_main_":
    link = "https://drive.google.com/file/d/1KEidGhXPIA6SeIrf92rnhB06k-PeysP-/view?usp=sharing"  # Replace with your link
    destination = "downloaded_file.zip"  # Specify your output file name
    download_file_from_google_drive(link, destination)
    print("import complete!")
