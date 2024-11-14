01 - BMI calculator https://drive.google.com/file/d/1QZ0YqwZrVU1uJW9TF2XfJsXfAsIFQWZF/view?usp=drive_link MainActivity.kt package com.example.myapplication import android.os.Bundle import androidx.activity.enableEdgeToEdge import androidx.appcompat.app.AppCompatActivity import androidx.core.view.ViewCompat import androidx.core.view.WindowInsetsCompat import androidx.lifecycle.findViewTreeViewModelStoreOwner import android.widget.Button import android.widget.EditText import android.widget.TextView class MainActivity : AppCompatActivity() { override fun onCreate(savedInstanceState: Bundle?) { super.onCreate(savedInstanceState) setContentView(R.layout.activity_main)

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
} activity_main.xml

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:id="@+id/main" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".MainActivity">

