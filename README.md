# EECS349HW3P3

Step 1:
The package name of the APK is "com.example.cs493.homework"

Step 2:
The apk uses the following permissions:
android.permission.GET_ACCOUNTS
android.permission.READ_PROFILE
android.permission.READ_CONTACTS
android.permission.CALL_PHONE
android.permission.SEND_SMS
android.permission.ACCESS_FINE_LOCATION

Answers for both Step 1 and Step 2 were found by inspecting the AndroidManifest.xml file of the unpacked APK.
(See Manifest.PNG for screenshot of the inspected manifest. The entier contents of the manifest is also included in the AndroidManifest.xml file in this repo)

Step 3:
In order to find the password that matched my username, I looked at the DEX byte code of the LoginActivity class. The file DEX byte code for LoginActivity.txt contains the full contents of this byte code. I have also commented all relevant lines to show how I came up with my answer.
From there I was able to deduce the following:
1. The entered username gets the string "@CS493" appended to the end
2. A variable X is instantated and starts at 1
3. We iterate over each charactor of the username (using iterator i) and set a variable X to the result of the following:

    X = (username.charAt(i) * X) % 12345678

    The decimal value 12345678 is found by converting 0xbc614e from HEX to Decimal

The password is equal to the string value of X once the loop finishes.

For Username "Seva", the password is "11278224"