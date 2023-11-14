# Opening an Android App with Extra Data using Two Different Methods

This web page serves as a testing and demonstration platform for opening an Android app with extra data using two different methods: URL Pattern and Intent Scheme.


## Preview the Site

To preview the functionality of the web page, visit [Karam Test App](https://karamzero.github.io).  


## Methods Overview

### 1. Open Android App using URL Pattern

- **Function:** `openAndroidAppUrlPattern()`
- **Description:** When the user clicks the "Open Android App using URL pattern" button, this method is triggered.
- **Action:** Constructs a URL with extra data (recipeId) and attempts to open it using a URL pattern (`https://karamzero.github.io/details?recipeId=<recipeId>`).
- **Goal:** Provides a standard way of opening a link on the web. If the Android app is configured to handle this URL pattern, it might prompt the user to open the app.

### 2. Open Android App with Intent Scheme

- **Function:** `openAndroidAppWithIntentScheme()`
- **Description:** When the user clicks the "Open Android App with Intent Scheme" button, this method is triggered.
- **Action:** Constructs a URL with extra data (recipeId) using the 'intent' scheme (`intent://karamzero.github.io/details?recipeId=<recipeId>#Intent;scheme=https;package=com.example.recipesapp;end`).
- **Intent Scheme:** Designed for communication between Android apps, it attempts to open the Android app directly.
- **Process:** The Android system checks if an app is registered to handle the 'intent' scheme with the specified package name and opens the app directly.
- **Advantage:** Provides a more direct and seamless transition between the web and the app.

## Prerequisites

Before implementing these methods, ensure that your Android app's activity, responsible for handling the intent, includes the following intent filter:

```xml
<intent-filter android:autoVerify="true">
    <action android:name="android.intent.action.VIEW" />
    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />
    
    <!-- Accepts URIs that begin with "https://karamzero.github.io/details” -->
    <!-- and with a query parameter "recipeId" ex https://karamzero.github.io/details?recipeId=12 -->
    <data android:scheme="https" />
    <data android:host="karamzero.github.io" />
    <data android:pathPattern="/details" />
    
    <!-- Add more schemes, hosts, and paths as needed -->

</intent-filter>

