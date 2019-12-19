# Linking activities in android studio 

The main objective is to demonstrate how to pass data between different activities. 

## What is an activity? 
An activity is an application component that provides a screen with which users can interact in order to do something, such as dial the phone, take a photo, send an email, or view a map. Each activity is given a window in which to draw its user interface.

## Current version:
  -Android Studio Version 3.5.2
  -Android SDK tool Version 26.1.1
  -Virtual device used = "Nexus 5X API 29 x86"
  


<img src="https://github.com/RattyMyles/Linking_Activities/blob/master/images/HomeScreenOfActivity.png" width="300" height="480"><img src="https://github.com/RattyMyles/Linking_Activities/blob/master/images/2ndActivity.png" width="300" height="480">


If you take a look at the layout XML files in this path:
```
Linking_Activities/app/src/main/res/layout/
```
It will show you how to create the text box, button and text view. 


## Mainactivity.java file

Within the main activity, the method below selects the xml object by ID. Using that ID I am able to grab the data input to pass to the next activity

```java
/** Called when the user taps the Send button */
    public void sendMessage(View view) {
        Intent intent = new Intent(this, DisplayMessageActivity.class);
        EditText editText = (EditText) findViewById(R.id.editText);
        String message = editText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivity(intent);
    }
```

## DisplayMessageActivity.java 

```java
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_display_message);

        // Get the Intent that started this activity and extract the string
        Intent intent = getIntent();
        String message = intent.getStringExtra(MainActivity.EXTRA_MESSAGE);

        // Capture the layout's TextView and set the string as its text
        TextView textView = findViewById(R.id.textView);
        textView.setText(message);
    }
    
```




