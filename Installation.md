# Installation Guide
Installation guide of botify 1 on local machine.

You can make use of any IDE of your choice or simply use command prompt or terminal.


Make sure to download and install the following dependenices.

## Dependencies
- [Oracle JDK 11](https://www.oracle.com/in/java/technologies/javase-jdk11-downloads.html)

- [Apache Maven](https://maven.apache.org/download.cgi)

- [Postgre SQL](https://www.postgresql.org/download/)

- [Liquibase](https://www.liquibase.org/download)

- Optional [VSCode](https://code.visualstudio.com/download)

## Setting up Botify
The following requires to have account in the respective platform mentioned.

Download the source code.

Botify makes use of 
- Discord

  1. Go to https://discordapp.com/developers/applications and create an application.
  
  2. Under **Bot** tab on the side menu to create a bot and copy the token.

  3. Paste it in the `resources/settings.properties` after `DISCORD_TOKEN=`.

  4. Under **Oauth2** tab on the side menu under **SCOPES** subsection check the `bot` checkbox.

  5. Under **BOT PERMISSIONS** subsection atleast check the following
  - Change Nickname
  - Send Messages
  - Manage Messages
  - Embed Links
  - Attach Files
  - Read Message History
  - Add Reactions
  - Connect
  - Speak

  6. Make sure to copy the link generated link below **SCOPES**.This is the link to add botify to your servers (you have to be an admin on the server).

- Spotify 
    1. Go to https://developer.spotify.com/dashboard/applications to create a Spotify application.

    2. Copy the **CLIENT ID** and **CLIENT SECRET**.

    3. Paste it in `resources/settings.properties` after `SPOTIFY_CLIENT_ID=` and `SPOTIFY_CLIENT_SECRET=` respectively.

    4. Click on **Edit Settings** and add "http://localhost:8000/login" under **Redirect URI**  section for the Spotify login.

- Youtube

    1. Go to https://console.developers.google.com/ and create a project.

    2. Click on **ENABLE APIS AND SERVICES** and search for **YouTube Data API v3** and enable it.

    3. Click on the *Google APIs* image and now under **ENABLE APIS AND SERVICES** side menu click on **Credentials**.
    
    4. Click on the **+ CREATE CREDENTIALS** and select **API Key** and copy the API key.

    5. Paste it in `resources/settings.properties` after `YOUTUBE_CREDENTIALS=`.

    6. For Botify to manage the YouTube API quota automatically, be sure to fill in the `YOUTUBE_API_DAILY_QUOTA property` in `resources/settings.properties`;
    Open the Google developer console and go to Library > YouTube Data API v3 > Manage > Quotas. Click on the **Quotas Page** link and find your daily quota.

- Orcale JDK 11

    Make sure to add JDK's bin path to environment variables.

- Apache Maven

    Make sure to add Maven's bin path to environment variables.

- Postgre SQL

    - Make sure to keep username and password as **postgres**.
    
    - After install open PgAdmin 4 under Servers > PostgreSQL 13.Right click on Databases and create a database as `botify_playlists`.

- Liquibase 

    Nothing required as long as the database name is same as mentioned above otherwise go to `src/main/resources/liquibase/liquibase.properties` and change it.


# Compile and run
The following can be done using IDE or cmd or terminal.

- Navigate to the project root directory and install botify by running `mvn clean install`. This will install project level dependencies.

- To run the bot 
  - Windows OS -  `mvn exec:java -D"exec.mainClass"="net.robinfriedli.botify.boot.Launcher"`.

  - Unix based OS - `mvn exec:java -Dexec.mainClass=net.robinfriedli.botify.boot.Launcher`.

- After you see the log **Launcher - All starters done** in the terminal click on the link you got in the 6 step of the discord setup and add the bot to your server.

- Now use the botify commands in discord to use the bot.