# View Binding

An example explaining how to use view binding, an null safe and type safe way to bind layout resources views.

## Setting up viewbinding

The first thing we'll have to do is to setup the view binding to our project. We will configure it on the build.gradle file from our app module:

```kotlin
android {
    ...
    buildFeatures {
        viewBinding true
    }
}
```

## Binding views

Then, every resource file created will have a generated class with the same name, in camelcase, with a Binding prefix. This class will have as atributes all the views from our layout file. To instanciate this class on an activity, we do it like this:

```kotlin
private lateinit var binding: ActivityMainBinding

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    binding = ActivityMainBinding.inflate(layoutInflater)
    setContentView(binding.root)

    binding.textView.text = "Hello Mars!!"
}
```

## Ignoring views

What we can also do is to ignore a view we do not want to see on our binding class. We do it by setting the tools:viewBindingIgnore property to true on our view:

```xml
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    tools:viewBindingIgnore="true"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
```
