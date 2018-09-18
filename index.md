---
layout: default
---
Get Started {#getting-started}
===========

::: {.meta}
:::

::: {.toctree}
Add Analytics \<add-aws-mobile-analytics\> Add User Sign-in
\<add-aws-mobile-user-sign-in\> Add Push Notifications
\<add-aws-mobile-push-notifications\> Add User File Storage
\<add-aws-mobile-user-data-storage\> Add Serverless Backend (AWS
AppSync) \<add-aws-mobile-serverless-backend\> Add Cloud Logic
\<add-aws-mobile-cloud-logic\> Add Messaging
\<add-aws-mobile-messaging\>
:::

::: {#add-aws-mobile-sdk}
Choose your platform:
:::

  ------------------------------------------------------------------------ ---------------------------------------------------------------------------- ------------------------------------------------------------------
  [![image](images/android-java.png)](getting-started.html#android-java)   [![image](images/android-kotlin.png)](getting-started.html#android-kotlin)   [![image](images/ios-swift.png)](getting-started.html#ios-swift)

  ------------------------------------------------------------------------ ---------------------------------------------------------------------------- ------------------------------------------------------------------

::: {.container .option}

Android - Java

:   ::: {#android-java}
    Get started building a cloud-powered Android app using the AWS
    Amplify CLI and the AWS SDK for Android. This page guides you
    through setting up an initial backend and integrating the SDK into
    your app.
    :::

Android - Kotlin

:   ::: {#android-kotlin}
    Get started building a cloud-powered Android app using the AWS
    Amplify CLI and the AWS SDK for Android. This page guides you
    through setting up an initial backend and integrating the SDK into
    your app.
    :::

iOS - Swift

:   ::: {#ios-swift}
    Get started building a cloud-powered iOS app using the AWS Amplify
    CLI and the AWS SDK for iOS. This page guides you through setting up
    an initial backend and integrating the SDK into your app.
    :::
:::

Step 1: Set Up Your Development Environment {#add-aws-mobile-sdk-basic-setup-prerequisites}
-------------------------------------------

We strongly recommend that you use the Amplify CLI for building the
serverless backend for your app. If you have already installed the CLI,
skip ahead to
`Step 2 <add-aws-mobile-sdk-basic-setup>`{.interpreted-text role="ref"}.

-   [Sign up for an AWS
    Account](https://portal.aws.amazon.com/billing/signup?redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start).
-   Install [Node.js](https://nodejs.org/) and npm (if they are not
    already installed).

::: {.note}
::: {.admonition-title}
Note
:::

Verify that you are running at least Node.js version 8.x or greater and
npm version 5.x or greater by running `node -v`{.sourceCode} and
`npm -v`{.sourceCode} in a terminal/console window. Older versions
aren\'t supported and might generate errors.
:::

To install and configure the Amplify CLI globally, run the following
commands in a terminal window.

``` {.sourceCode .bash}
$ npm install -g @aws-amplify/cli

$ amplify configure
```

Minimum requirements for your development environment are as follows.

> ::: {.container .option}
>
> Android - Java
>
> :   -   Choose the Android Java app project you want to integrate with
>         an AWS backend.
>     -   [Install Android
>         Studio](https://developer.android.com/studio/index.html#downloads)
>         version 2.33 or higher.
>     -   Install Android SDK for API level 23 (Android SDK 6.0).
>
> Android - Kotlin
>
> :   -   Choose the Android Kotlin app project you want to integrate
>         with an AWS backend.
>     -   [Install Android
>         Studio](https://developer.android.com/studio/index.html#downloads)
>         version 2.33 or higher.
>     -   Install Android SDK for API level 23 (Android SDK 6.0).
>
> iOS - Swift
>
> :   -   Choose the iOS app project you want to integrate with an AWS
>         backend.
>     -   [Install Xcode](https://developer.apple.com/xcode/downloads/)
>         version 8.0 or later.
> :::

Step 2: Set Up Your Backend {#add-aws-mobile-sdk-basic-setup}
---------------------------

1.  The CLI prompts you for configuration parameters.

    > ::: {.container .option}
    >
    > Android - Java
    >
    > :   In a terminal window, navigate to your project folder (the
    >     folder that typically contains your project level
    >     `build.gradle`{.interpreted-text role="file"}), and add the
    >     SDK to your app.
    >
    > > ``` {.sourceCode .none}
    > > $ cd ./YOUR_PROJECT_FOLDER
    > > $ amplify init
    > > ```
    >
    > Android - Kotlin
    >
    > :   In a terminal window, navigate to your project folder (the
    >     folder that typically contains your project level
    >     `build.gradle`{.interpreted-text role="file"}), and add the
    >     SDK to your app.
    >
    > > ``` {.sourceCode .none}
    > > $ cd ./YOUR_PROJECT_FOLDER
    > > $ amplify init
    > > ```
    >
    > iOS - Swift
    >
    > :   In a terminal window, navigate to your project folder (the
    >     folder that typically contains your project level
    >     `xcodeproj`{.interpreted-text role="file"} file), and add the
    >     SDK to your app.
    >
    > > ``` {.sourceCode .none}
    > > $ cd ./YOUR_PROJECT_FOLDER
    > > $ amplify init
    > > ```
    > :::

2.  To create your backend AWS resources and add a configuration file to
    your app, run the following:

    ::: {.container .option}

    Android - Java

    :   ``` {.sourceCode .bash}
        $ amplify push
        ```

    Android - Kotlin

    :   ``` {.sourceCode .none}
        $ amplify push
        ```

    iOS - Swift

    :   ``` {.sourceCode .none}
        $ amplify push
        ```

        In the Finder, navigate to the folder containing your app
        `.xcodeproj`{.interpreted-text role="file"} file. From there,
        drag `awsconfiguration.json`{.sourceCode} to Xcode under the top
        Project Navigator folder (the folder name should match your
        Xcode project name). In the `Options`{.interpreted-text
        role="guilabel"} dialog box that appears, do the following:

        -   Clear the `Copy items if needed`{.interpreted-text
            role="guilabel"} check box.
        -   Choose `Create groups`{.interpreted-text role="guilabel"},
            and then choose `Next`{.interpreted-text role="guilabel"}.
    :::

3.  To verify that the CLI is set up for your app, run the following
    command. The CLI displays a status table with no resources listed.
    As you add categories to your app, backend resources created for
    your app are listed in this table.

    ``` {.sourceCode .none}
    $ amplify status
    | Category | Resource name | Operation | Provider plugin |
    | -------- | ------------- | --------- | --------------- |
    ```

    Use the steps in the next section to configure the connection
    between your app and the serverless backend.

Step 3: Connect to Your Backend {#add-aws-mobile-sdk-connect-to-your-backend}
-------------------------------

Perform the following steps to set up a connection to AWS services that
you\'ll use in the Get Started section of this guide.

::: {.container .option}

Android - Java

:   1.  Add dependencies to your `app/build.gradle`{.interpreted-text
        role="file"}, and then choose `Sync Now`{.interpreted-text
        role="guilabel"} on the upper-right side of Android Studio.
        These libraries enable basic AWS functions, like credentials and
        analytics.

        ``` {.sourceCode .java}
        dependencies {
            implementation 'com.amazonaws:aws-android-sdk-core:2.6.+'
        }
        ```

    2.  Your `AndroidManifest.xml`{.interpreted-text role="file"} must
        contain the following:

        ``` {.sourceCode .xml}
        <uses-permission android:name="android.permission.INTERNET"/>
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
        ```

    Your app is now ready for you to add cloud-powered features. We
    recommend
    `adding analytics <add-aws-mobile-analytics>`{.interpreted-text
    role="ref"} as your first feature.

Android - Kotlin

:   1.  Add dependencies to your `app/build.gradle`{.interpreted-text
        role="file"}, and then choose `Sync Now`{.interpreted-text
        role="guilabel"} on the upper-right side of Android Studio.
        These libraries enable basic AWS functions, like credentials and
        analytics.

        ``` {.sourceCode .java}
        dependencies {
            implementation 'com.amazonaws:aws-android-sdk-core:2.6.+'
        }
        ```

    2.  Your `AndroidManifest.xml`{.interpreted-text role="file"} must
        contain the following:

        ``` {.sourceCode .xml}
        <uses-permission android:name="android.permission.INTERNET"/>
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
        ```

    Your app is now ready for you to add cloud-powered features. We
    recommend
    `adding analytics <add-aws-mobile-analytics>`{.interpreted-text
    role="ref"} as your first feature.

iOS - Swift

:   1.  Install Cocoapods. From a terminal window run the following:

        ``` {.sourceCode .none}
        sudo gem install cocoapods
        ```

    2.  Create `Podfile`{.interpreted-text role="file"}. From a terminal
        window, navigate to the directory that contains your project\'s
        `.xcodeproj`{.interpreted-text role="file"} file and run the
        following:

        > ``` {.sourceCode .none}
        > pod init
        > ```

    3.  Open `Podfile`{.interpreted-text role="file"} in a text editor
        and add the pod for core AWS Mobile SDK components to your
        build.

        ``` {.sourceCode .none}
        platform :ios, '9.0'
        target :'YOUR-APP-NAME' do
            use_frameworks!

            pod 'AWSCore', '~> 2.6.13'

            # other pods
        end
        ```

    4.  Install dependencies by running the following:

        ``` {.sourceCode .none}
        pod install --repo-update
        ```

        If you encounter an error message that begins
        \"`[!] Failed to connect to GitHub to update the CocoaPods/Specs . . .`{.sourceCode}\",
        and your internet connectivity is working, you might need to
        [update openssl and
        Ruby](https://stackoverflow.com/questions/38993527/cocoapods-failed-to-connect-to-github-to-update-the-cocoapods-specs-specs-repo/48962041#48962041).

    5.  The command `pod install`{.sourceCode} creates a new workspace
        file. Close your Xcode project and reopen it using
        `./YOUR-PROJECT-NAME.xcworkspace`{.interpreted-text
        role="file"}.

          -------------- ------------------------------------------------------------
          Use **ONLY**   Remember to always use
          your           `./YOUR-PROJECT-NAME.xcworkspace`{.interpreted-text
          .xcworkspace   role="file"} to open your Xcode project from now on.

          -------------- ------------------------------------------------------------

    6.  Rebuild your app after reopening it in the workspace to resolve
        APIs from new libraries called in your code. This is a good
        practice any time you add import statements.

    Your app is now ready for you to add cloud-powered features. We
    recommend
    `adding analytics <add-aws-mobile-analytics>`{.interpreted-text
    role="ref"} as your first feature.
:::

Next Steps {#add-aws-mobile-sdk-next-steps}
----------

> -   `Add Analytics <add-aws-mobile-analytics>`{.interpreted-text
>     role="ref"}
> -   `Add User Sign-in <add-aws-mobile-user-sign-in>`{.interpreted-text
>     role="ref"}
> -   `Add Push Notification <add-aws-mobile-push-notifications>`{.interpreted-text
>     role="ref"}
> -   `Add User File Storage <add-aws-mobile-user-data-storage>`{.interpreted-text
>     role="ref"}
> -   `Add Serverless Backend <add-aws-mobile-serverless-backend>`{.interpreted-text
>     role="ref"}
> -   `Add Cloud Logic <add-aws-mobile-cloud-logic>`{.interpreted-text
>     role="ref"}
> -   `Add Messaging <add-aws-mobile-messaging>`{.interpreted-text
>     role="ref"}
