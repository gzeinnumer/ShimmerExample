# ShimmerExample

- depedencies
```gradle
implementation 'com.facebook.shimmer:shimmer:0.4.0@aar'
```
- colors.xml
```xml
<color name="background">#dddddd</color>
```
- dimens.xml
```xml
<dimen name="activityPadding">16dp</dimen>
<dimen name="placeholderImage">60dp</dimen>
<dimen name="placeholderTextHeight">8dp</dimen>
<dimen name="padding_10">10dp</dimen>
```

- [shimmer_card.xml](https://github.com/gzeinnumer/ShimmerExample/blob/master/app/src/main/res/layout/shimmer_card.xml)

- [shimmer_parent.xml](https://github.com/gzeinnumer/ShimmerExample/blob/master/app/src/main/res/layout/shimmer_parent.xml)

- activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:shimmer="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <com.facebook.shimmer.ShimmerFrameLayout
        android:id="@+id/shimmer_view_container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="center"
        android:layout_marginTop="15dp"
        android:orientation="vertical"
        android:visibility="visible"
        shimmer:duration="800"
        tools:visibility="gone">

        <include layout="@layout/shimmer_parent" />

    </com.facebook.shimmer.ShimmerFrameLayout>

    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Repeat Shimmer" />
</LinearLayout>
```

- MainActivity.java
```java
public class MainActivity extends AppCompatActivity {
    ShimmerFrameLayout shimmerFrameLayout;
    Button button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        shimmerFrameLayout = findViewById(R.id.shimmer_view_container);
        button = findViewById(R.id.btn);

        shimmer();

        button.setOnClickListener(v -> shimmer());
    }

    private void shimmer() {
        shimmerFrameLayout.setVisibility(View.VISIBLE);
        shimmerFrameLayout.startShimmer();
        new CountDownTimer(3000, 1000) {

            public void onTick(long millisUntilFinished) {
            }

            public void onFinish() {
                shimmerFrameLayout.stopShimmer();
                shimmerFrameLayout.setVisibility(View.GONE);
            }
        }.start();
    }
}
```

- Preview

![](https://github.com/gzeinnumer/ShimmerExample/blob/master/preview/example1.gif)

---

```
Copyright 2021 M. Fadli Zein
```