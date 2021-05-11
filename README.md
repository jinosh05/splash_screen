# splash_screen_view

They say, first impression is the last! Yep, truly for any amazingly crafted application, it's easier to start impressing your audience with a good start - the splash screen!

Every time a flutter application is started, it takes some time to load the Dart isolate (which runs the code). This means user will see a blank white screen till Flutter renders the first frame of the application.

Use this package automatically generates android, iOS, and Web native code for customizing this native splash screen background color and splash image. Supports dark mode, full screen, and platform-specific options.

The native splash screen is displayed till Flutter renders the first frame of the application. After that you have to load your real splash screen.

This package also contains a collection of Splash Screen example for your application to display logo and different style of text.

<table>
<tr><th>Before Splash screen</th><th>After Splash screen</th></tr>
<tr><td><img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/Before_Splash.gif?raw=true" height = "400px"></td><td><img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/After_Splash.gif?raw=true" align = "right" height = "400px"></td></tr>
</table>

# Installing

### 1. Depend on it
Add this to your package's `pubspec.yaml` file:

```yaml
dependencies:
  splash_screen_view: ^3.0.0
```

### 2. Install it

You can install packages from the command line:

with `pub`:

```css
$ pub get
```

with `Flutter`:

```css
$ flutter packages get
```

### 3. Setting the splash screen

Customized the following settings and add to your project's `pubspec.yaml` file.

```yaml
splash_screen_view:
  # Use color to set the background of your splash screen to a solid color.
  # Use background_image to set the background of your splash screen to a png image.
  # This is useful for gradients. The image will be stretch to the  size of the app.
  # Only one parameter can be used, color and background_image cannot both be set.

  color: "#ffffff"
  #background_image: "assets/splashscreen_image.png"

  # Optional parameters are listed below.
  #image: assets/splashscreen_image.png

  #color_dark: "#042a49"
  #background_image_dark: "assets/dark-background.png"
  #image_dark: assets/splash-invert.png

  #android: false
  #ios: false
  #web: false

  #android_gravity: center
  #ios_content_mode: center
  #web_image_mode: center

  #fullscreen: true

  #info_plist_files:
  #  - 'ios/Runner/Info-Debug.plist'
  #  - 'ios/Runner/Info-Release.plist'
```
### 4. Run the package

After adding your settings, run the following command in the terminal:

```dart
flutter pub run splash_screen_view:create
```

When the package finishes running, your splash screen is ready.


# Usage of Splash Screen View

## Import it

Now in your `Dart` code, you can use:

```dart
import 'package:splash_screen_view/SplashScreenView.dart';
```

## Simple Logo

<img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/OnlyImage.gif?raw=true" align = "right" height = "400px">

```dart
SplashScreenView(
      navigateRoute: SecondScreen(),
      duration: 3000,
      imageSize: 130,
      imageSrc: "logo.png",
      backgroundColor: Colors.white,
    );
```
[Where]:
 - navigateRoute (required)- Name of target screen which you want to display after completion of splash screen milliseconds.
 - duration - Delay between the splash screen and target screen. Provider Duration in millisecond.
 - imageSrc - Assets path for your logo which your want to display on splash screen.
 - imageSize - Size of your logo. By default it is 150.
 - backgroundColor - Background color of splash screen. By default it is white color.


## Logo with Text

<img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/Normal.gif?raw=true" align = "right"  height = "400px">

```dart
SplashScreenView(
      navigateRoute: SecondScreen(),
      duration: 3000,
      imageSize: 130,
      imageSrc: "logo.png",
      text: "Splash Screen",
      textType: TextType.NormalText,
      textStyle: TextStyle(
        fontSize: 30.0,
      ),
      backgroundColor: Colors.white,
    );
```
[Where]:
 - text - Text which you want to show below logo.
 - textType - Gives text type as TextType.NormalText
 - textStyle - Gives TextStyle to the text strings.
**Note:** Give `imageSrc` as blank If you want only text on your splash screen.

## Colorize Animated Text

<img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/ColorizeAnimatedText.gif?raw=true" align = "right"  height = "400px">

```dart
SplashScreenView(
      navigateRoute: SecondScreen(),
      duration: 5000,
      imageSize: 130,
      imageSrc: "logo.png",
      text: "Splash Screen",
      textType: TextType.ColorizeAnimationText,
      textStyle: TextStyle(
        fontSize: 40.0,
      ),
      colors: [
        Colors.purple,
        Colors.blue,
        Colors.yellow,
        Colors.red,
      ],
      backgroundColor: Colors.white,
    );
```
[Where]:
 - textType - Gives text type as TextType.ColorizeAnimationText
 - colors - Set the colors for the gradient animation of the text. Give List with values of [Color] in it.
**Note:** `colors` list should contains at least two values.


## Scale Animated Text

<img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/ScaleAnimatedText.gif?raw=true" align = "right"  height = "400px">

```dart
SplashScreenView(
      navigateRoute: SecondScreen(),
      duration: 3000,
      imageSize: 130,
      imageSrc: "logo.png",
      text: "Splash Screen",
      textType: TextType.ScaleAnimatedText,
      textStyle: TextStyle(
        fontSize: 30.0,
      ),
      backgroundColor: Colors.white,
    );
```
[Where]:
 - textType - Gives text type as TextType.ScaleAnimatedText


## Typer Animated Text

<img src="https://github.com/SandipVKalola/splash_screen/blob/master/display/TyperAnimatedText.gif?raw=true" align = "right"  height = "400px">

```dart
SplashScreenView(
      navigateRoute: SecondScreen(),
      duration: 3000,
      imageSize: 130,
      imageSrc: "logo.png",
      text: "Splash Screen",
      textType: TextType.TyperAnimatedText,
      textStyle: TextStyle(
        fontSize: 30.0,
      ),
      backgroundColor: Colors.white,
    );
```
[Where]:
 - textType - Gives text type as TextType.TyperAnimatedText


## Page Route Behaviors
Defines standard behaviors when transitioning between routes (or screens). Sometimes, though, a custom transition between screens can make an app more unique.

Support of page route behaviors
 - pageRouteTransition: PageRouteTransition.Normal
 - pageRouteTransition: PageRouteTransition.CupertinoPageRoute
 - pageRouteTransition: PageRouteTransition.SlideTransition


# How it works
## Android
* Your splash image will be resized to `mdpi`, `hdpi`, `xhdpi`, `xxhdpi` and `xxxhdpi` drawables.
* An `<item>` tag containing a `<bitmap>` for your splash image drawable will be added in `launch_background.xml`
* Background color will be added in `colors.xml` and referenced in `launch_background.xml`.
* Code for full screen mode toggle will be added in `styles.xml`.
* Dark mode variants are placed in `drawable-night`, `values-night`, etc. resource folders.

## iOS
* Your splash image will be resized to `@3x` and `@2x` images.
* Color and image properties will be inserted in `LaunchScreen.storyboard`.
* The background color is implemented by using a single pixel png file and stretching it to fit the screen.
* Code for hidden status bar toggle will be added in `Info.plist`.

## Web
* A `web/splash` folder will be created for splash screen images and CSS files.
* Your splash image will be resized to `1x`, `2x`, and `3x` sizes and placed in `web/splash/img`.
* The splash style sheet will be added to the app's `web/index.html`, as well as the HTML for the splash pictures.

# Removing

If you would like to restore Flutter's default white splash screen, run the following command in the terminal:

```
flutter pub run splash_screen_view:remove
```


# Bugs or Requests

If you encounter any problems feel free to open an [issue](https://github.com/SandipVKalola/splash_screen/issues/new?template=bug_report.md). If you feel the library is missing a feature, please raise a [ticket](https://github.com/SandipVKalola/splash_screen/issues/new?template=feature_request.md) on GitHub and I'll look into it. Pull request are also welcome.


# Acknowledgments

Automatically generates android, iOS, and Web native code was originally created by [Henrique Arthur](https://github.com/henriquearthur) and it is currently maintained by [Jon Hanson](https://github.com/jonbhanson).

## Github example link
https://github.com/SandipVKalola/splash_screen

# Donate
> If you found this project helpful or you learned something from the source code and want to thank me, consider buying me a cup of :coffee:
>
> - [PayPal](https://paypal.me/sandipkalola)

# License
Splash Screen is licensed under `MIT license`. View [license](https://github.com/SandipVKalola/splash_screen/blob/master/LICENSE).
