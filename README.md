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
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Quantidade de litros de combustível"
        android:textSize="25sp"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Tempo gasto"
        android:textSize="25dp"
        />
   <EditText
       android:layout_width="match_parent"
       android:layout_height="wrap_content"
       android:id="@+id/Tempog"
       />
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Velocidade media"
        android:textSize="25dp"
        />
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/velocidade"
        />
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="media"
        android:textSize="25dp"
        />
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/media"
        />
    <Button
        android:id="@+id/calcular"
        android:layout_width="359dp"
        android:layout_height="106dp"
        android:text="Calcular"
        android:textSize="25dp"/>
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
       android:id="@+id/Tvresultado"
        />

</LinearLayout>



package com.example.xms2;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private EditText media,tempo,velocidade;
    private TextView Tvresultado;
    private Button calcular;
    @Override
    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {

            media = findViewById(R.id.media);
            tempo = findViewById(R.id.Tempog);
            velocidade = findViewById(R.id.velocidade);
            calcular = findViewById(R.id.calcular);
            Tvresultado = findViewById(R.id.Tvresultado);


            calcular.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
              double distancia = Double.parseDouble(tempo.getText().toString()) * Double.parseDouble(velocidade.getText().toString());
              double litros = distancia / Double.parseDouble(media.getText().toString());
              Tvresultado.setText(String.valueOf(litros));



                }
            });


            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
    }
}
