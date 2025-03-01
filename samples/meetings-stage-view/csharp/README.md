---
page_type: sample
description: Enable and configure your apps for Teams meetings to use in stage view
products:
- office-teams
- office
- office-365
languages:
-  csharp
extensions:
 contentType: samples
 createdDate: "21/10/2022 19:03:46"
urlFragment: officedev-microsoft-teams-samples-meetings-stage-view-csharp
---

# Meetings Stage View

This App helps to enable and configure your apps for Teams meetings. This app covers Shared meeting stage using [Live Share SDK](https://aka.ms/livesharedocs).
For reference please check [Enable and configure your apps for Teams meetings](https://docs.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings)

## Interaction with app- Mobile

![Preview Image](Images/preview_web.gif)

## Interaction with app- Web

![Preview Image](Images/preview_mobile.gif)


## Prerequisites

- [.NET Core SDK](https://dotnet.microsoft.com/download) version 6.0

  determine dotnet version
  ```bash
  dotnet --version
  ```
- [Ngrok](https://ngrok.com/download) (For local environment testing) Latest (any other tunneling software can also be used)
  
- [Teams](https://teams.microsoft.com) Microsoft Teams is installed and you have an account


## Setup.

**This capability is currently available in developer preview only**


1. Register a new application in the [Azure Active Directory – App Registrations](https://go.microsoft.com/fwlink/?linkid=2083908) portal.
    > NOTE: When you create your app registration, you will create an App ID and App password - make sure you keep these for later.


2. Setup NGROK
- Run ngrok - point to port 3978

```bash
# ngrok http -host-header=rewrite 3978
```

3. Setup for code

- Clone the repository

    ```bash
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

 - In a terminal, navigate to `samples/meetings-stage-view/csharp`

    ```bash
    # change into project folder
    cd # AppInMeeting
    ```

- Inside ClientApp folder execute the below command.

    ```bash
    # npx @fluidframework/azure-local-service@latest
    ```
    
- Run the app from a terminal or from Visual Studio, choose option A or B.

  A) From a terminal

  ```bash
  # run the app
  dotnet run
  ```

  B) Or from Visual Studio

  - Launch Visual Studio
  - File -> Open -> Project/Solution
  - Navigate to `AppInMeeting` folder
  - Select `AppInMeeting.csproj` file
  - Press `F5` to run the project

## Getting the App id for share to stage deeplink.

1) Navigate to [Teams admin portal]("https://admin.teams.microsoft.com/dashboard")

2) Under Teams Apps section, select Manage apps.

3) Search the uploaded app and copy the `App ID`
![Admin Center](Images/adminCenter.png)

4) Navigate to `samples/meetings-stage-view/csharp/AppInMeeting/ClientApp/src/components/app-in-meeting.jsx`

5) On line 41, replace `<<App id>>` with `Id` obtained in step 3.

5. Setup Manifest for Teams
- __*This step is specific to Teams.*__
    - **Edit** the `manifest.json` contained in the ./AppPackage folder to replace your Microsoft App Id (that was created when you registered your app registration earlier) *everywhere* you see the place holder string `{{Microsoft-App-Id}}` (depending on the scenario the Microsoft App Id may occur multiple times in the `manifest.json`)
    - **Edit** the `manifest.json` for `validDomains` and replace `{{domain-name}}` with base Url of your domain. E.g. if you are using ngrok it would be `https://1234.ngrok.io` then your domain-name will be `1234.ngrok.io`.
    - **Zip** up the contents of the `AppPackage` folder to create a `manifest.zip` (Make sure that zip file does not contains any subfolder otherwise you will get error while uploading your .zip package)

- Upload the manifest.zip to Teams (in the Apps view click "Upload a custom app")
   - Go to Microsoft Teams. From the lower left corner, select Apps
   - From the lower left corner, choose Upload a custom App
   - Go to your project directory, the ./AppPackage folder, select the zip folder, and choose Open.
   - Select Add in the pop-up dialog box. Your app is uploaded to Teams.

## Running the sample
    You can use this app by following the below steps:
       - Edit a meeting and select `+` icon at the top right corner.

- App in stage view.

![Stage View Screen](Images/stage_view.png)

- Sharing specific part of your app to the meeting stage.

![Share Specific part screen](Images/share_specific_part.png)

**NOTE: Currently Live Share SDK is not supported in mobiles.**

## Android Meeting Side panel and stage view.

![IOS Side Panel](Images/ios_side_panel.jpeg)

![IOS Stage View](Images/ios_share_todo.jpeg)

## Android Meeting Side panel and stage view.

![Android Side Panel](Images/android_side_panel.jpeg)

![Android Stage View](Images/android_share_todo.jpeg)

![Add icon in meeting](Images/add_icon.png)

    - Search for your app `App in meeting` and add it.

![Select App](Images/select_app.png)

    - Join the meeting and click on the app icon at the top
    - This will open a sidepanel with `Share` icon at top to share the app for collaboration in stage view.

![App icon](Images/app_icon.png)

![Share Icon](Images/share_icon.png)

    - You can now interact with the app.


- Add Details for collaboration.

![Add Button](Images/add_button.png)

![Add Details](Images/add_details.png)

- App in sidepanel.

![App in sidepanel](Images/side_panel.png)

- Sharing specific parts of app.

![Share specific part](Images/share_specific_part_sidepanel.png)

## Further Reading.

[Meeting stage view](https://learn.microsoft.com/en-us/microsoftteams/platform/sbs-meetings-stage-view)

[Deeplink to meeting share to stage](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/build-apps-for-teams-meeting-stage#generate-a-deep-link-to-share-content-to-stage-in-meetings)
