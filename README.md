# Prevernir-que-el-Bottom-navigation-oculte-el-contenido-Java-Android

# Solucion No. 1

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <LinearLayout
        android:id="@+id/ecrMainCoordinator"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:fitsSystemWindows="true"
        android:layout_above="@+id/ecrNavigation"
        android:orientation="vertical">

        <android.support.constraint.ConstraintLayout
            android:id="@+id/ecrMainCos"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            >
            <TextView
                android:id="@+id/ecrTitleCompany"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginEnd="16dp"
                android:layout_marginLeft="16dp"
                android:layout_marginRight="16dp"
                android:layout_marginStart="16dp"
                android:layout_marginTop="16dp"
                android:gravity="center_horizontal"
                android:text="@string/str_company"
                android:textColor="@android:color/black"
                android:textSize="@dimen/text24"
                android:maxLength="20"
                android:maxLines="1"
                android:ellipsize="end"
                android:textStyle="bold"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <ImageButton
                android:id="@+id/ecrBtnCloseSession"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginEnd="16dp"
                android:layout_marginRight="16dp"
                android:layout_marginTop="16dp"
                android:contentDescription="@string/str_info"
                android:background="?attr/selectableItemBackgroundBorderless"
                android:clickable="true"
                android:focusable="true"
                android:onClick="closeSession"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintTop_toTopOf="parent"
                app:srcCompat="@drawable/logout" />


            <View
                android:id="@+id/ecrDivider"
                android:layout_width="match_parent"
                android:layout_height="1dp"
                android:layout_marginEnd="16dp"
                android:layout_marginLeft="16dp"
                android:layout_marginRight="16dp"
                android:layout_marginStart="16dp"
                android:layout_marginTop="8dp"
                android:background="@color/divider"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toBottomOf="@+id/ecrTitleCompany" />

            <TextView
                android:id="@+id/ecrTitleSection"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginEnd="16dp"
                android:layout_marginLeft="16dp"
                android:layout_marginRight="16dp"
                android:layout_marginStart="16dp"
                android:layout_marginTop="16dp"
                android:text="@string/str_title_section"
                android:textColor="@android:color/black"
                android:textSize="@dimen/text20"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toBottomOf="@+id/ecrDivider" />

            <TextView
                android:id="@+id/ecrSubtitleSection"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginEnd="16dp"
                android:layout_marginLeft="16dp"
                android:layout_marginRight="16dp"
                android:layout_marginStart="16dp"
                android:text="@string/str_section_subtitle"
                android:textColor="@android:color/black"
                android:textSize="@dimen/text16"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintHorizontal_bias="0.0"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toBottomOf="@+id/ecrTitleSection" />
        </android.support.constraint.ConstraintLayout>

        <FrameLayout
            android:id="@+id/ecrFrameContent"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_behavior="@string/appbar_scrolling_view_behavior" />
    </LinearLayout>

    <android.support.design.widget.BottomNavigationView
        android:id="@+id/ecrNavigation"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginEnd="0dp"
        android:layout_marginStart="0dp"
        android:background="@android:color/white"
        app:labelVisibilityMode="labeled"
        android:layout_alignParentBottom="true"
        app:menu="@menu/navigation" />

</RelativeLayout>
```

# Solución No. 2

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true"
    tools:context=".MainActivity">

    <android.support.design.widget.CoordinatorLayout
        android:id="@+id/container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:fitsSystemWindows="true"
        android:layout_above="@+id/navigation">

        <android.support.design.widget.AppBarLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:theme="@style/AppTheme.AppBarOverlay">

            <!-- Use this to hide appbar on scroll - app:layout_scrollFlags="scroll|enterAlways" -->
            <android.support.v7.widget.Toolbar
                android:id="@+id/toolbar"
                android:layout_width="match_parent"
                android:layout_height="?attr/actionBarSize"
                android:background="?attr/colorPrimary"
                app:popupTheme="@style/AppTheme.PopupOverlay" />

        </android.support.design.widget.AppBarLayout>

        <!-- this could be a RecyclerView or NestedScrollView -->
        <FrameLayout
            android:id="@+id/content"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_behavior="@string/appbar_scrolling_view_behavior"
            >

        </FrameLayout>

        <android.support.design.widget.FloatingActionButton
            android:id="@+id/fab"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="bottom|end"
            android:layout_margin="@dimen/fab_margin"
            app:tint="@android:color/white"
            app:srcCompat="@drawable/ic_photo_camera_black_24dp" />

    </android.support.design.widget.CoordinatorLayout>

    <android.support.design.widget.BottomNavigationView
        android:id="@+id/navigation"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:background="?android:attr/windowBackground"
        app:menu="@menu/navigation"
         />

</RelativeLayout>
```

Source: https://code.luasoftware.com/tutorials/android/android-prevent-bottomnavigationview-cover-content/
