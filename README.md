// MainActivity.java // تطبيق زامدار - Java Android App

package com.zamdar.app;

import android.content.Intent; import android.graphics.Color; import android.os.Bundle; import android.view.Gravity; import android.view.View; import android.widget.Button; import android.widget.EditText; import android.widget.ImageView; import android.widget.LinearLayout; import android.widget.ScrollView; import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity; import androidx.cardview.widget.CardView;

public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    LinearLayout root = new LinearLayout(this);
    root.setOrientation(LinearLayout.VERTICAL);
    root.setBackgroundColor(Color.parseColor("#0F3B2E"));
    root.setPadding(40, 80, 40, 40);
    root.setGravity(Gravity.CENTER);

    ImageView logo = new ImageView(this);
    logo.setImageResource(android.R.drawable.ic_menu_agenda);
    LinearLayout.LayoutParams logoParams = new LinearLayout.LayoutParams(200, 200);
    logo.setLayoutParams(logoParams);

    TextView title = new TextView(this);
    title.setText("زامدار");
    title.setTextColor(Color.WHITE);
    title.setTextSize(32);
    title.setGravity(Gravity.CENTER);

    TextView subtitle = new TextView(this);
    subtitle.setText("مكتبة الكتب الدينية");
    subtitle.setTextColor(Color.LTGRAY);
    subtitle.setTextSize(18);
    subtitle.setGravity(Gravity.CENTER);

    EditText email = new EditText(this);
    email.setHint("البريد الإلكتروني");
    email.setBackgroundColor(Color.WHITE);
    email.setPadding(20, 20, 20, 20);

    LinearLayout.LayoutParams fieldParams = new LinearLayout.LayoutParams(
            LinearLayout.LayoutParams.MATCH_PARENT,
            LinearLayout.LayoutParams.WRAP_CONTENT
    );
    fieldParams.setMargins(0, 30, 0, 0);
    email.setLayoutParams(fieldParams);

    EditText password = new EditText(this);
    password.setHint("كلمة المرور");
    password.setBackgroundColor(Color.WHITE);
    password.setPadding(20, 20, 20, 20);
    password.setLayoutParams(fieldParams);

    Button loginButton = new Button(this);
    loginButton.setText("تسجيل الدخول");
    loginButton.setTextColor(Color.BLACK);
    loginButton.setBackgroundColor(Color.parseColor("#D4AF37"));
    loginButton.setLayoutParams(fieldParams);

    loginButton.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent intent = new Intent(MainActivity.this, HomeActivity.class);
            startActivity(intent);
        }
    });

    root.addView(logo);
    root.addView(title);
    root.addView(subtitle);
    root.addView(email);
    root.addView(password);
    root.addView(loginButton);

    setContentView(root);
}

}

// HomeActivity.java

package com.zamdar.app;

import android.graphics.Color; import android.os.Bundle; import android.view.Gravity; import android.widget.GridLayout; import android.widget.LinearLayout; import android.widget.ScrollView; import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity; import androidx.cardview.widget.CardView;

public class HomeActivity extends AppCompatActivity {

String[] categories = {
        "القرآن الكريم",
        "التفسير",
        "الحديث",
        "العقيدة",
        "الفقه",
        "الأذكار",
        "السيرة",
        "الدعاء"
};

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    ScrollView scrollView = new ScrollView(this);

    LinearLayout root = new LinearLayout(this);
    root.setOrientation(LinearLayout.VERTICAL);
    root.setPadding(20, 20, 20, 20);
    root.setBackgroundColor(Color.parseColor("#F6F2E9"));

    TextView title = new TextView(this);
    title.setText("زامدار");
    title.setTextSize(28);
    title.setTextColor(Color.parseColor("#0F3B2E"));
    title.setGravity(Gravity.CENTER);
    title.setPadding(0, 20, 0, 30);

    GridLayout gridLayout = new GridLayout(this);
    gridLayout.setColumnCount(2);

    for (String category : categories) {
        CardView card = new CardView(this);

        GridLayout.LayoutParams params = new GridLayout.LayoutParams();
        params.width = 450;
        params.height = 250;
        params.setMargins(20, 20, 20, 20);
        card.setLayoutParams(params);
        card.setRadius(25);
        card.setCardBackgroundColor(Color.WHITE);

        TextView text = new TextView(this);
        text.setText(category);
        text.setTextSize(18);
        text.setTextColor(Color.parseColor("#0F3B2E"));
        text.setGravity(Gravity.CENTER);

        card.addView(text);
        gridLayout.addView(card);
    }

    root.addView(title);
    root.addView(gridLayout);

    scrollView.addView(root);

    setContentView(scrollView);
}

}
