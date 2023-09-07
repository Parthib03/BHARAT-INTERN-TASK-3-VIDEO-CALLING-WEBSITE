# Agora Web RTC Token Generator

This README file provides instructions on how to generate an Agora Web RTC token with a channel name set to "main" in the `main.js` file before running the HTML file. It's essential to renew the Web RTC token every 24 hours for secure and uninterrupted communication.

## Prerequisites

Before proceeding, make sure you have the following prerequisites in place:

- An Agora developer account.
- Agora Web SDK integrated into your project.

## Getting Started

Follow these steps to generate an Agora Web RTC token for your project:

1. **Access Your Agora Dashboard**: Log in to your Agora developer account and access the dashboard.

2. **Create a New Project**: If you haven't already, create a new project in your Agora dashboard. This project will be associated with your application.

3. **Generate an App ID**: Within the project, generate an App ID. This ID will be required for authentication.

4. **Integrate Agora Web SDK**: Ensure you have integrated the Agora Web SDK into your project. You can follow the official Agora documentation for guidance on this step.

5. **Update `main.js`**:

   In your project's `main.js` file, set the channel name to "main." This is the channel where your Web RTC communication will take place. You can use the following code snippet as an example:

   ```javascript
   // Set the channel name to "main"
   const channelName = "main";
   ```

6. **Token Generation Script**:

   Now, you need to generate a Web RTC token for authentication. Use the Agora Web SDK to generate the token with the appropriate permissions. Here's an example of how you can do this:

   ```javascript
   // Import the Agora SDK and initialize it with your App ID
   const agora = require('agora-rtc-sdk');
   const client = agora.createClient({ mode: 'rtc', codec: 'vp8' });
   client.init('YOUR_APP_ID');

   // Define user role and privilege expiration time
   const role = agora.RtcRole.PUBLISHER;
   const expirationTimeInSeconds = 3600; // 1 hour, adjust as needed

   // Generate the token
   const token = agora.generateAccessToken(YOUR_APP_ID, YOUR_APP_CERTIFICATE, channelName, null, uid, role, expirationTimeInSeconds);
   ```

   Replace `YOUR_APP_ID` and `YOUR_APP_CERTIFICATE` with your actual App ID and App Certificate from your Agora project.

7. **Token Renewal**:

   It's crucial to renew the Web RTC token every 24 hours (or sooner, depending on your security requirements). Implement a mechanism to refresh the token in your application code.

## Running the Application

After setting up and generating the Web RTC token, you can run your HTML file. Ensure that the `main.js` file is properly configured with the channel name and the token generation logic.

By following these steps, you can securely authenticate and run your Agora Web RTC application with the "main" channel. Remember to keep your tokens updated for seamless communication.
