smsemail

MainActivity.kt




class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        var phno:EditText=findViewById(R.id.phno)
        var msg:EditText=findViewById(R.id.msg)
        var btn:Button=findViewById(R.id.btn)
        btn.setOnClickListener{
            if(ActivityCompat.checkSelfPermission(this,Manifest.permission.SEND_SMS)!=PackageManager.PERMISSION_GRANTED){
                requestPermissions(arrayOf(Manifest.permission.SEND_SMS),2)

            }
            val mobno=phno.getText().toString()
            var message=msg.getText().toString()
            val smsMessage= SmsManager.getDefault()
            smsMessage.sendTextMessage(mobno,null,message,null,null)
            Toast.makeText(this,"SMS SEND SUCCESSFULLY",Toast.LENGTH_LONG).show()
        }
    }
}

xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/phno"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="12dp"
        android:ems="10"
        android:hint="Enter phone no"
        android:inputType="text"
        app:layout_constraintEnd_toEndOf="@+id/textView2"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <EditText
        android:id="@+id/msg"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:ems="10"
        android:hint="Enter message"
        android:inputType="text"
        app:layout_constraintStart_toStartOf="@+id/phno"
        app:layout_constraintTop_toBottomOf="@+id/phno" />

    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginTop="38dp"
        android:text="Send sms"
        app:layout_constraintStart_toStartOf="@+id/msg"
        app:layout_constraintTop_toBottomOf="@+id/msg" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="69dp"
        android:layout_marginTop="16dp"
        android:text="SENDING SMS"
        android:textColor="#E41414"
        android:textSize="34sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

manifest

 <uses-permission android:name="android.permission.SEND_SMS"/>
    <uses-feature android:name="android.hardware.telephony"/>


Bluetooth paired


class MainActivity : AppCompatActivity() {
    private lateinit var tvDevices: TextView
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        val button:Button = findViewById(R.id.button)
        val listView:ListView = findViewById(R.id.listView)
        val bluetoothAdapter:BluetoothAdapter =
            BluetoothAdapter.getDefaultAdapter()
        if(checkSelfPermission(android.Manifest.permission.BLUETOOTH_CONNECT)!=
            PackageManager.PERMISSION_GRANTED) {
            requestPermissions(arrayOf(android.Manifest.permission.BLUETOOTH_CONNECT),
                1)
        }
        button.setOnClickListener {
            val pairedDevices: Set<BluetoothDevice> =
                bluetoothAdapter.bondedDevices
            val deviceList = mutableListOf<String>()
            if (pairedDevices.isNotEmpty()) {
                for (device in pairedDevices) {
                    deviceList.add("${device.name} (${device.address})")
                }
                val adapter = ArrayAdapter(this,
                    android.R.layout.simple_list_item_1, deviceList)
                listView.adapter = adapter
            } else {
                Toast.makeText(this, "No paired devices found",
                    Toast.LENGTH_SHORT).show()
            }
        }
    }
}


xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:orientation="vertical"
    >
    <Button
        android:id="@+id/button"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:text="View Paired Devices"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="50dp"
        />
    <ListView
        android:id="@+id/listView"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_marginTop="20dp"
        android:padding="20dp"
        />
</LinearLayout>

gradle
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.jetbrains.kotlin.android)
}

android {
    namespace = "com.example.ex9"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.example.ex9"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    kotlinOptions {
        jvmTarget = "1.8"
    }
}

dependencies {

    implementation("androidx.core:core-ktx:1.12.0") // Switch to 1.12.0
    implementation(libs.androidx.appcompat)
    implementation(libs.material)
    implementation(libs.androidx.activity)
    implementation(libs.androidx.constraintlayout)

    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)
}


manifest

<uses-permission android:name="android.permission.BLUETOOTH_CONNECT" />



basic

package com.example.basic

import android.os.Bundle
import android.widget.*
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initialize UI elements
        val editText: EditText = findViewById(R.id.editText)
        val spinner: Spinner = findViewById(R.id.spinner)
        val radioGroup: RadioGroup = findViewById(R.id.radioGroup)
        val checkBox: CheckBox = findViewById(R.id.checkBox)
        val button: Button = findViewById(R.id.button)
        val displayText: TextView = findViewById(R.id.displayText)

        // Spinner items
        val spinnerItems = arrayOf("Item 1", "Item 2", "Item 3")
        val spinnerAdapter = ArrayAdapter(this, android.R.layout.simple_spinner_dropdown_item, spinnerItems)
        spinner.adapter = spinnerAdapter

        // Button click listener
        button.setOnClickListener {
            val name = editText.text.toString()
            val selectedSpinnerItem = spinner.selectedItem.toString()

            // Get the selected RadioButton if any
            val selectedRadioButtonId = radioGroup.checkedRadioButtonId
            val selectedRadioButton: RadioButton? = if (selectedRadioButtonId != -1) {
                findViewById(selectedRadioButtonId)
            } else null

            // Get Checkbox status
            val isChecked = checkBox.isChecked

            // Prepare display message
            val displayMessage = """
                Name: $name
                Spinner: $selectedSpinnerItem
                Radio Button: ${selectedRadioButton?.text ?: "None"}
                Checkbox: ${if (isChecked) "Checked" else "Unchecked"}
            """.trimIndent()

            // Display the result in TextView
            displayText.text = displayMessage
        }
    }
}


xml

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name" />

    <Spinner
        android:id="@+id/spinner"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <RadioGroup
        android:id="@+id/radioGroup"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <RadioButton
            android:id="@+id/radioButton1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Option 1" />

        <RadioButton
            android:id="@+id/radioButton2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Option 2" />
    </RadioGroup>

    <CheckBox
        android:id="@+id/checkBox"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Check me" />

    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Submit" />

    <TextView
        android:id="@+id/displayText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@android:color/black" />

</LinearLayout>



camera

MainActivity.kt

class MainActivity : AppCompatActivity() {

    private lateinit var imageView: ImageView
    private lateinit var btnCapture: Button
    private lateinit var photoUri: Uri
    private var photoFile: File? = null

    private val cameraLauncher: ActivityResultLauncher<Intent> =
        registerForActivityResult(ActivityResultContracts.StartActivityForResult())
        { result ->
            if (result.resultCode == RESULT_OK && photoFile != null) {
                val bitmap = BitmapFactory.decodeFile(photoFile!!.absolutePath)
                imageView.setImageBitmap(bitmap)
                Toast.makeText(this,photoFile!!.absolutePath,Toast.LENGTH_LONG).show()
            } else {
                Toast.makeText(this, "Capture cancelled", Toast.LENGTH_SHORT).show()
            }
        }


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        imageView = findViewById(R.id.imageView)
        btnCapture = findViewById(R.id.btn)

        btnCapture.setOnClickListener {
            val cameraPermission = ActivityCompat.checkSelfPermission(this, Manifest.permission.CAMERA)
            val storagePermission = ActivityCompat.checkSelfPermission(this, Manifest.permission.WRITE_EXTERNAL_STORAGE)

            if(cameraPermission == PackageManager.PERMISSION_GRANTED && storagePermission == PackageManager.PERMISSION_GRANTED){
                capturePhoto()
            }
            else {
                val permissions = mutableListOf(Manifest.permission.CAMERA)
                if (Build.VERSION.SDK_INT < Build.VERSION_CODES.TIRAMISU) {
                    permissions.add(Manifest.permission.WRITE_EXTERNAL_STORAGE)
                }
                requestPermissions(permissions.toTypedArray(), 101)
            }

        }
    }

    override fun onRequestPermissionsResult(requestCode: Int, permissions: Array<out String>, grantResults: IntArray) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults)
        if (requestCode == 101 && grantResults.isNotEmpty() && grantResults.all { it == PackageManager.PERMISSION_GRANTED }) {
            capturePhoto()
        }
        else {
            Toast.makeText(this, "Permissions denied", Toast.LENGTH_SHORT).show()
        }
    }



    private fun capturePhoto() {
        val intent = Intent(MediaStore.ACTION_IMAGE_CAPTURE)
        val timeStamp: String = SimpleDateFormat("yyyyMMdd_HHmmss").format(Date())
        val storageDir: File? = getExternalFilesDir(Environment.DIRECTORY_PICTURES)
        photoFile = File.createTempFile("JPEG_${timeStamp}_", ".jpg", storageDir)
        if(photoFile != null) {
            photoUri = FileProvider.getUriForFile(this, "${applicationContext.packageName}.provider", photoFile!!)
            intent.putExtra(MediaStore.EXTRA_OUTPUT, photoUri)
            cameraLauncher.launch(intent)
        }
    }
}


xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:orientation="vertical"
    >

    <Button
        android:id="@+id/btn"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:text="Take Photo"
        android:layout_marginTop="50dp"
        android:layout_gravity="center_horizontal"
        />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="300dp"
        android:layout_height="400dp"
        tools:srcCompat="@tools:sample/avatars"
        android:layout_marginTop="20dp"
        android:layout_gravity="center_horizontal"

        />

</LinearLayout>

file_paths.xml
<?xml version="1.0" encoding="utf-8"?>
<paths xmlns:android="http://schemas.android.com/apk/res/android">
    <external-path name="images" path="." />
</paths>

manifest
<uses-feature
        android:name="android.hardware.camera"
        android:required="false" />
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>


<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.camera"
        android:required="false" />
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Cameras"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- Move the provider here, outside of the activity -->
        <provider
            android:name="androidx.core.content.FileProvider"
            android:authorities="${applicationId}.provider"
            android:exported="false"
            android:grantUriPermissions="true">
            <meta-data
                android:name="android.support.FILE_PROVIDER_PATHS"
                android:resource="@xml/file_paths" />
        </provider>

    </application>
</manifest>



sensor
mainactivity.kt

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        val btn:Button = findViewById(R.id.viewBtn)
        val listView: ListView = findViewById(R.id.listView)
        val sensorManager = getSystemService(Context.SENSOR_SERVICE) as
                SensorManager
        btn.setOnClickListener {

            val sensorManager = getSystemService(Context.SENSOR_SERVICE)
                    as SensorManager

            val sensorList: List<Sensor> =
                sensorManager.getSensorList(Sensor.TYPE_ALL)

            val sensorNames = sensorList.map { it.name }



            val adapter = ArrayAdapter(this,
                android.R.layout.simple_list_item_1, sensorNames)
            listView.adapter = adapter
        }
    }
}

xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    tools:context=".MainActivity"
    android:orientation="vertical">
    <Button
        android:id="@+id/viewBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="View All Sensors"
        android:layout_marginTop="40dp"
        android:layout_gravity="center_horizontal"
        />
    <ListView
        android:id="@+id/listView"
        android:layout_width="379dp"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="20dp"
        android:textColor="#D81B60"
        android:textSize="25dp"
        />
</LinearLayout>



notification


class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
// Create notification channel (only needed once)
        createNotificationChannel(this)
        val btn:Button=findViewById(R.id.button)
        btn.setOnClickListener {
// Show notification when needed
            showNotification(this)
        }
    }
    fun createNotificationChannel(context: Context) {
        if(Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            val name = "MyNotificationChannel"
            val descriptionText = "This is my notification channel"
            val importance = NotificationManager.IMPORTANCE_DEFAULT
            val channel = NotificationChannel("my_channel_1", name, importance)
            channel.description = descriptionText
// Register the channel with the system
            val notificationManager: NotificationManager =
                context.getSystemService(Context.NOTIFICATION_SERVICE) as
                        NotificationManager
            notificationManager.createNotificationChannel(channel)
        }
    }
    fun showNotification(context: Context) {

        val intent = Intent(context, ResponseActivity::class.java)
        intent.putExtra("msg","This is the notification content")
        val pendingIntent: PendingIntent =
            PendingIntent.getActivity(context, 0,

                intent,PendingIntent.FLAG_IMMUTABLE )
// Build the notification
        val builder = NotificationCompat.Builder(context,
            "my_channel_1")

            .setContentTitle("Notification Title")
            .setContentText("This is the notification content")
            .setPriority(NotificationCompat.PRIORITY_HIGH)
            .setVisibility(NotificationCompat.VISIBILITY_PUBLIC)
            .setContentIntent(pendingIntent)
            .setAutoCancel(true)
            .build()
//Runtime permission request
// Show the notification
        val notificationManager =
            NotificationManagerCompat.from(context)
        if (ActivityCompat.checkSelfPermission(
                this,
                Manifest.permission.POST_NOTIFICATIONS
            ) != PackageManager.PERMISSION_GRANTED
        ) {
            // TODO: Consider calling
            //    ActivityCompat#requestPermissions
            // here to request the missing permissions, and then overriding
            //   public void onRequestPermissionsResult(int requestCode, String[] permissions,
            //                                          int[] grantResults)
            // to handle the case where the user grants the permission. See the documentation
            // for ActivityCompat#requestPermissions for more details.
            return
        }
        notificationManager.notify(1, builder)
    }
}


xml activity
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="204dp"
        android:text="Send Notification"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>

response.kt

import android.os.Bundle
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
class ResponseActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_response)
        val response:TextView = findViewById(R.id.response)
        if(intent!=null) {
            response.text = intent.getStringExtra("msg")
        }
    }
}

xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"

    android:layout_height="match_parent"
    tools:context=".ResponseActivity">
    <TextView
        android:id="@+id/response"
        android:layout_width="335dp"
        android:layout_height="55dp"
        android:layout_marginTop="68dp"
        android:ems="10"
        android:textColor="#D81B60"
        android:textSize="18dp"
        android:textAlignment="center"
        android:gravity="center_horizontal"
        android:inputType="textMultiLine"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>

manifest
<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />


