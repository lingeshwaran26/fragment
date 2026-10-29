# Practical 4: Fragment Creation and Fragment Lifecycle Demonstration

Develop an Android application to create and integrate a Fragment and demonstrate Fragment lifecycle methods using Logcat.

---

## Project Overview

* **Project Name:** FragmentLifecycleDemo
* **Template:** Empty Views Activity
* **Language:** Java
* **Package Name:** `com.example.fragmentlifecycledemo`
* **Fragment Creation:** `java > new > fragment > Fragment (Blank)`
  * **Fragment Name:** `DemoFragment`
  * **Fragment Layout Name:** `fragment_demo`

---

## 1. Java Source Code
**Path:** `app > java > com > example > fragmentlifecycledemo >`

### I. `DemoFragment.java`
```java
package com.example.fragmentlifecycledemo;

import android.content.Context;
import android.os.Bundle;
import android.util.Log;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;

public class DemoFragment extends Fragment {

    String TAG = "FragmentLifecycle";

    @Override
    public void onAttach(@NonNull Context context) {
        super.onAttach(context);
        Log.d(TAG, "onAttach() executed");
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        Log.d(TAG, "onCreate() executed");
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        Log.d(TAG, "onCreateView() executed");
        return inflater.inflate(R.layout.fragment_demo, container, false);
    }

    @Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);
        Log.d(TAG, "onViewCreated() executed");
    }

    @Override
    public void onStart() {
        super.onStart();
        Log.d(TAG, "onStart() invoked");
    }

    @Override
    public void onResume() {
        super.onResume();
        Log.d(TAG, "onResume() invoked");
    }

    @Override
    public void onPause() {
        super.onPause();
        Log.d(TAG, "onPause() invoked");
    }

    @Override
    public void onStop() {
        super.onStop();
        Log.d(TAG, "onStop() invoked");
    }

    @Override
    public void onDestroyView() {
        super.onDestroyView();
        Log.d(TAG, "onDestroyView() executed");
    }

    @Override
    public void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "onDestroy() executed");
    }

    @Override
    public void onDetach() {
        super.onDetach();
        Log.d(TAG, "onDetach() executed");
    }
}
```

### II. `MainActivity.java`
```java
package com.example.fragmentlifecycledemo;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.FragmentTransaction;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        DemoFragment fragment = new DemoFragment();
        FragmentTransaction transaction = getSupportFragmentManager().beginTransaction();
        transaction.replace(R.id.fragment_container_view_tag, fragment);
        transaction.commit();
    }
}
```

---

## 2. Layout XML Files
**Path:** `app > res > layout >`

### I. `activity_main.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout android:id="@+id/fragment_container_view_tag" android:layout_height="match_parent" android:layout_width="match_parent" xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)"/>
```

### II. `fragment_demo.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout android:layout_height="match_parent" android:layout_width="match_parent" tools:context=".DemoFragment" xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)" xmlns:tools="[http://schemas.android.com/tools](http://schemas.android.com/tools)">

    <TextView android:layout_gravity="center" android:layout_height="wrap_content" android:layout_width="wrap_content" android:text="Demo Fragment Loaded" android:textSize="20sp" android:textStyle="bold"/>

</FrameLayout>
```

---

## 3. Logcat Execution Instructions

1. **Run the App:** Click the green **Play (Run)** button at the top toolbar in Android Studio.
2. **Open Logcat:** Click the **Logcat** tab at the bottom toolbar (or press `Alt + 6` / `Cmd + 6`).
3. **Filter Logs:** In the search/filter bar of Logcat, type `FragmentLifecycle`.
4. **Lifecycle Verification Steps:**
   * **Fragment Loaded:** Observe `onAttach()`, `onCreate()`, `onCreateView()`, `onViewCreated()`, `onStart()`, and `onResume()`.
   * **Press Home Button:** Observe `onPause()` and `onStop()`.
   * **Re-open App:** Observe `onStart()` and `onResume()`.
   * **Press Back Button:** Observe `onPause()`, `onStop()`, `onDestroyView()`, `onDestroy()`, and `onDetach()`.
