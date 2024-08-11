# One Tap Google Sign-In with Jetpack Compose

This repository demonstrates the implementation of One Tap Google Sign-In using Jetpack Compose in an Android app. The project utilizes the [stevdza-san](https://github.com/stevdza-san/OneTapCompose) dependency for easy integration of Google sign-in functionality.

## Features

- One Tap Google Sign-In using Jetpack Compose
- Customizable UI for the sign-in button
- Easy retrieval of Google user information

## Getting Started

### Prerequisites

1. **Google Cloud Platform Setup**:
   - Go to the [Google Cloud Console](https://console.cloud.google.com/).
   - Create a new project or select an existing one.
   - Navigate to **APIs & Services > Credentials**.
   - Create an OAuth 2.0 Client ID and add your app's SHA-1 fingerprint.
   - Copy the Client ID and replace the `YOUR CLIENT ID` placeholder in the code with your Client ID.

2. **Gradle**:
   - **Dependencies**:
     This project uses the `stevdza-san` dependency for One Tap Google Sign-In. Make sure to include it in your `build.gradle` file:
     ```kotlin
     dependencies {
         implementation("com.github.stevdza-san:OneTapCompose:1.0.14")
     }
     ```

     - - **settings.gradle**:

     ```kotlin
     dependencyResolutionManagement {
          repositories {
              ...
              maven(url = "https://jitpack.io")
          }
     }
     ```

3. Usage

   Replace `YOUR CLIENT ID` with the client ID you copied from Google Cloud:
   ```kotlin
   val state = rememberOneTapSignInState()
   var user: GoogleUser? by remember { mutableStateOf(null) }
   
   OneTapSignInWithGoogle(
       state = state,
       clientId = "YOUR CLIENT ID", // Replace with your client ID
       rememberAccount = false,
       onTokenIdReceived = {
           user = getUserFromTokenId(tokenId = it)
           Log.d("MainActivity", user.toString())
       },
       onDialogDismissed = {
           Log.d("MainActivity", it)
       }
   )
   
   Box(
       modifier = Modifier.fillMaxSize(),
       contentAlignment = Alignment.Center
   ) {
       Button(onClick = { state.open() }) {
           Row(verticalAlignment = Alignment.CenterVertically) {
               if (state.opened) {
                   CircularProgressIndicator(
                       color = Color.White
                   )
               }
               Spacer(modifier = Modifier.width(8.dp))
               Text(text = "Sign in")
           }
       }
   }
   ```

### Running the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/Bhavyansh03-tech/One_Tap_Google_Sign_In.git
   ```
2. Open the project in Android Studio.

3. Replace the YOUR CLIENT ID in the MainActivity.kt file with your actual Google Client ID from the Google Cloud Console.

4. Build and run the project on your Android device or emulator.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -am 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Create a new Pull Request.

## Contact

For questions or feedback, please contact [@Bhavyansh03-tech](https://github.com/Bhavyansh03-tech).

---
