
This project serve as a reference project demonstrating the architecture, tools and guidelines that we use in [InDataCore](https://indatacore.com/) when developing new Android projects.


# Architecture

This project follows InDataCore's Android architecture guidelines that are based on [MVVM (Model View ViewModel)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel). Read more about it [here](guidelines/architecture_guidelines/architecture_guidelines.md). 

![](./guidelines/images/mvvm_architecture.png)

# Main Libraries & Tools

Libraries and tools included:

- Support libraries
- RecyclerViews and CardViews 
- [RxJava](https://github.com/ReactiveX/RxJava) and [RxAndroid](https://github.com/ReactiveX/RxAndroid) 
- [Retrofit 2](http://square.github.io/retrofit/)
- [Dagger 2](http://google.github.io/dagger/)
- [SqlBrite](https://github.com/square/sqlbrite)
- [Butterknife](https://github.com/JakeWharton/butterknife)
- [Timber](https://github.com/JakeWharton/timber)
- [Glide](https://github.com/bumptech/glide)
- [AutoValue](https://github.com/google/auto/tree/master/value) with extensions [AutoValueParcel](https://github.com/rharter/auto-value-parcel) and [AutoValueGson](https://github.com/rharter/auto-value-gson)
- Functional tests with [Espresso](https://google.github.io/android-testing-support-library/docs/espresso/index.html)
- [Robolectric](http://robolectric.org/)
- [Mockito](http://mockito.org/)
- [Checkstyle](http://checkstyle.sourceforge.net/), [PMD](https://pmd.github.io/) and [Findbugs](http://findbugs.sourceforge.net/) for code analysis


# Code Quality

This project integrates a combination of unit tests, functional test and code analysis tools. 

## Tests

To run **unit** tests on your machine:

``` 
./gradlew test
``` 

To run **functional** tests on connected devices:

``` 
./gradlew connectedAndroidTest
``` 

Note: For Android Studio to use syntax highlighting for Automated tests and Unit tests you **must** switch the Build Variant to the desired mode.

## Code Analysis tools 

The following code analysis tools are set up on this project:

* [PMD](https://pmd.github.io/): It finds common programming flaws like unused variables, empty catch blocks, unnecessary object creation, and so forth. See [this project's PMD ruleset](config/quality/pmd/pmd-ruleset.xml).

``` 
./gradlew pmd
```

* [Findbugs](http://findbugs.sourceforge.net/): This tool uses static analysis to find bugs in Java code. Unlike PMD, it uses compiled Java bytecode instead of source code.

```
./gradlew findbugs
```

* [Checkstyle](http://checkstyle.sourceforge.net/): It ensures that the code style follows [our Android code guidelines](./guidelines/code_style_guidelines/code_style_guidelines.md). See our [checkstyle config file](config/quality/checkstyle/checkstyle-config.xml).

```
./gradlew checkstyle
```

## The check task

To ensure that your code is valid and stable use check: 

```
./gradlew check
```

This will run all the code analysis tools and unit tests in the following order:

![Check Diagram](./guidelines/images/check-task-diagram.png)


### Play Store

We will use the __Gradle Play Publisher__ plugin. Once set up correctly, you will be able to push new builds to
the Alpha, Beta or production channels like this

```
./gradlew publishApkRelease
```
Read [plugin documentation](https://github.com/Triple-T/gradle-play-publisher) for more info.

### Crashlytics



## New project setup 

To quickly start a new project from this boilerplate follow the next steps:

* Download this [repository as a zip](https://indatacore.com/starter-project/master.zip).
* Change the package name. 
  * Rename packages in main, androidTest and test using Android Studio.
  * In `app/build.gradle` file, `packageName` and `testInstrumentationRunner`.
  * In `src/main/AndroidManifest.xml` and `src/debug/AndroidManifest.xml`.
* Create a new [Gitlab](https://skyanalytics.indatacore.com:4041/) repository.
* Replace the example code with your app code following the same architecture.
* In `app/build.gradle` add the signing config to enable release versions.
* Update `proguard-rules.pro` to keep models (see TODO in file) and add extra rules to file if needed.
* Update README with information relevant to the new project.
* Update LICENSE to match the requirements of the new project.

## Requirements

- JDK 1.8
- [Android SDK](http://developer.android.com/sdk/index.html).
- Android 5.0 [(API 21) ](http://developer.android.com/tools/revisions/platforms.html).
- Latest Android SDK Tools and build tools.

# android-sdk-30-jdk-11
