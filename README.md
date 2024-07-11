### Secure File Transfer App Documentation

---

#### Overview

The Secure File Transfer App is designed to provide a secure and efficient method for transferring files. Users can upload files, set a time for their availability, and then securely send a URL to the file via an SMTP server. The architecture is built to ensure the security and integrity of the file and the credentials used. 


#### Components

1. **Frontend**
    - **Flask (Web Server)**: Serves the user interface for file uploads, credential input, and scheduling settings.
    - **User Authentication**: Implements secure user authentication to protect access to the app.

2. **Python Logic**
    - **Main Code**: Core logic that handles file processing, interactions with the database, encryption, and communication with other services.
    - **Encryption**: Encrypts files and encodes file names before storage.

3. **MongoDB**
    - **Database**: Stores file metadata, user data, and application data.
    - **Data Storage**: Keeps records of uploaded files, including their associated URLs, timers, and encryption details.

4. **Bash Logic**
    - **Timer and Trigger**: Handles timing and triggering events for sending file URLs at the specified time.
    - **Enhanced Logging**: Implements detailed logging for monitoring and troubleshooting.

5. **SMTP (Cloud)**
    - **Email Service**: Uses an SMTP server, such as Gmail for testing, to send the file URL to the specified email address securely.

6. **User Input**
    - **Credentials**: Users input their email credentials for authenticating the SMTP server.
    - **File Upload**: Users upload files, set upload limits, and specify allowed file types.

7. **Key Management Solution**
    - **Huds Key Management Solution**: Securely saves and encrypts credentials on the server, storing them in a Key Database (KDB).

---

#### Workflow

1. **File Upload and Timer Set**
    - User accesses the web interface and logs in.
    - User uploads the file, sets upload limits, and specifies allowed file types.
    - User sets a time for when the URL to the file should be sent.

2. **Credential Input**
    - User enters email credentials required to authenticate the SMTP server.
    - Credentials are securely pulled from the Huds Key Management Solution.

3. **File Processing and Storage**
    - Uploaded file is encrypted, and its name is encoded before storage.
    - File metadata is stored in MongoDB.

4. **Email Sending**
    - At the specified time, the Bash logic triggers the Python script to send the URL.
    - The SMTP server is used to send an email with the URL to the recipient.

5. **Security Management**
    - All credentials and sensitive information are securely managed and encrypted.
    - Enhanced logging tracks all activities for monitoring and troubleshooting.

---

#### Security Features

1. **User Authentication**
    - Ensures only authorized users can access the app and upload files.
    - Uses secure authentication mechanisms.

2. **Encryption**
    - Files are encrypted before storage.
    - File names are encoded to prevent unauthorized access.

3. **Key Management**
    - Huds Key Management Solution securely stores and encrypts user credentials.

4. **File Upload Limits and Restrictions**
    - Users can specify upload limits and allowed file types to prevent abuse.

5. **Enhanced Logging**
    - Detailed logging for all activities to monitor and troubleshoot security issues.

---

#### Threat Modeling and Security Mechanisms

1. **Threat Modeling**

    - **Threats Identified**:
        - Unauthorized access to uploaded files.
        - Credential theft during SMTP communication.
        - Data leakage from the database.
        - Abuse of file upload functionality.

    - **Attack Vectors**:
        - Brute force attacks on user authentication.
        - Man-in-the-middle attacks during email transmission.
        - SQL injection attacks on MongoDB.
        - Uploading malicious files.

2. **Security Mechanisms**

    - **User Authentication**:
        - Implement multi-factor authentication (MFA) to enhance security.
        - Use secure password storage mechanisms (e.g., bcrypt).

    - **Encryption**:
        - Use AES-256 encryption for file storage.
        - Ensure secure key management with Huds Key Management Solution.

    - **Communication Security**:
        - Use TLS/SSL to secure SMTP communication.
        - Encrypt credentials during transmission.

    - **Database Security**:
        - Implement input validation and parameterized queries to prevent SQL injection.
        - Encrypt sensitive data stored in MongoDB.

    - **File Upload Security**:
        - Restrict allowed file types and enforce size limits.
        - Scan uploaded files for malware.

    - **Logging and Monitoring**:
        - Implement detailed logging for all activities.
        - Monitor logs for suspicious activities and anomalies.

---

#### Future Enhancements

1. **User Authentication**
    - Implement more robust authentication mechanisms and support for federated identity providers.

2. **Enhanced Logging**
    - Add more granular logging and integrate with SIEM systems for real-time monitoring.

3. **Multi-file Support**
    - Extend the app to support multiple file uploads in a single session with individual timers.

4. **Advanced Scheduling**
    - Provide more advanced scheduling options for sending file URLs, including recurring schedules and timezone support.

---
