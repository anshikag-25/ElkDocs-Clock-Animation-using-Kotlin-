# ElkDocs-Clock-Animation-using-Kotlin-
ClockAnimation

Clock Animation App is a Jetpack Compose application that displays a vibrant, animated clock with dynamic, vibrating circles around it. The app features animated clock hands, a changing background stroke, and vibrant circles that provide an eye-catching effect.

Features

Animated Clock Hands: The seconds and minutes hands of the clock rotate smoothly.
Dynamic Background Stroke: The outer circle changes color dynamically to create a striking visual effect.
Vibrating Circles: Multiple circles vibrate and change size and color around the clock, enhancing the visual appeal.

Demo Video
https://github.com/user-attachments/assets/95266d20-2eaf-4a0a-87ec-9883767a177a

Getting Started
Prerequisites
Android Studio Jellyfish or later
Kotlin
Android SDK 29 or later

Installation
1. Clone the repository.
   
2. Open the project in Android Studio:

 Navigate to the project directory and open it in Android Studio.

3. Build the project:

Click on the Build option in the top menu and select Make Project.

4. Run the application:

Connect your Android device or start an emulator. Click on the Run button in Android Studio.

Code Structure

MainActivity

The MainActivity sets up the content view and enables edge-to-edge display. It also configures the status bar appearance.

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            ClockAnimationTheme {
                SideEffect {
                    val window = this@MainActivity.window
                    window.statusBarColor = Color.Black.toArgb()
                    WindowCompat.getInsetsController(window, window.decorView)
                        .isAppearanceLightStatusBars = false
                }
                Surface(color = Color.Black) {
                    AnimatedScreen()
                }
            }
        }
    }
}


Composables

AnimatedScreen: The main screen composable that contains the background stroke, vibrating circles, and the animated clock.

AnimatedClock: A composable that displays the clock with animated hands.

BackgroundStroke: A composable that draws the dynamic outer circle around the clock.

VibratingCirclesScreen: A composable that sets up the vibrating circles.

VibratingCircles: A composable that draws the vibrating circles around the clock.

Animations

Clock Hands: The seconds and minutes hands rotate using animateFloat.

Background Stroke: The outer circle's color changes using animateColor.

Vibrating Circles: Each circle vibrates and changes color and size using animateColor and animateFloat.

Customization

Adjusting the Number of Circles

You can adjust the number of vibrating circles by changing the numberOfCircles parameter in the AnimatedScreen composable:

AnimatedScreen(clockSize = 200.dp, numberOfCircles = 10)

Changing Circle Size Factor

You can change the size factor of the vibrating circles by adjusting the sizeFactor parameter in the VibratingCircles composable:

VibratingCircles(modifier = Modifier.fillMaxSize(), numberOfCircles = numberOfCircles, sizeFactor = 2.5f) 

Build Configuration
Plugins
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.jetbrains.kotlin.android)
}
Android Configuration
android {
    namespace = "com.example.clockanimation"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.example.clockanimation"
        minSdk = 29
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
        vectorDrawables {
            useSupportLibrary = true
        }
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    kotlinOptions {
        jvmTarget = "1.8"
    }
    buildFeatures {
        compose = true
    }
    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.1"
    }
    packaging {
        resources {
            excludes += "/META-INF/{AL2.0,LGPL2.1}"
        }
    }
}
Dependencies
dependencies {
    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.lifecycle.runtime.ktx)
    implementation(libs.androidx.activity.compose)
    implementation(platform(libs.androidx.compose.bom))
    implementation(libs.androidx.ui)
    implementation(libs.androidx.ui.graphics)
    implementation(libs.androidx.ui.tooling.preview)
    implementation(libs.androidx.material3)
    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)
    androidTestImplementation(platform(libs.androidx.compose.bom))
    androidTestImplementation(libs.androidx.ui.test.junit4)
    debugImplementation(libs.androidx.ui.tooling)
    debugImplementation(libs.androidx.ui.test.manifest)
}

Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

Fork the repository

Create your feature branch (git checkout -b feature/AmazingFeature)

Commit your changes (git commit -m 'Add some amazing feature')

Push to the branch (git push origin feature/AmazingFeature)

Open a pull request

Contact

If you have any questions or suggestions, feel free to reach out to me at anshika2005.ag@gmail.com


