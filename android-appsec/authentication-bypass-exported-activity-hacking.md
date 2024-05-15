# Authentication Bypass (Exported Activity Hacking )

1. **Retrieve the APK File**: Obtain the target APK file that you want to analyze.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

1.  **Install APK on the Android Emulator**

    &#x20;

    <figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
2.  **Decompile APK using Apktool**

    <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
3.  **Decode APK Contents**

    <figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
4.  **Analyze** `AndroidManifest.xml`: Investigate the `AndroidManifest.xml` file to identify declared activities and their associated permissions, Notice that there is exported Activities.

    <figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
5.  **Exploration of Application Features**: Launch the application on the emulator to interact with its functionalities, Notice it is simple password manageer.

    <figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
6.  **Identify Authentication Requirements**: Note any authentication mechanisms required by the application, such as password length or two-factor authentication (2FA) PIN.

    <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
7.  **Access Password List Activity**: Discover the Password List Activity mentioned in the `AndroidManifest` file, where passwords and account details are managed&#x20;

    <figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
8.  **Attempt to Access Exported Activities**: Use the Activity Manager (am start -n ) to try accessing exported activities from outside the application

    <figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
9. **Investigate Potential Data Storage Locations**: Start file list activity and searching for any data leakage, but found nothing + i couldn't access other activities from there.
10. **Access Password List Activity**: Successfully access the Password List Activity from outside the application

    <figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
11. **Encounter Error Messages**: Encounter error messages when attempting to view or modify passwords due to a required service not being started.&#x20;

    <figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
12. **Examine Settings and Backup Options**: Investigate settings options within the application to create backups of passwords
13. **Discover Backup File Accessibility**: Find that backup files can be accessed via another exported activity, `com.mwr.example.sieve/.FileSelectActivity`


14. **Identify Security Vulnerability**: Realize that plaintext passwords are accessible without authentication, potentially exposing users to password theft through malicious apps.

    <figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
15. I will let the part of creating APP POC for you ;)