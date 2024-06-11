# Dermektyw - an application to diagnose skin diseases using your phone camera and AI!

With some simple UI, the power of the application lays behind the code - using a local server hosted Tensorflow model, the application allows its user to take a photo of their skin and diagnose one of three groups of diseases:
- Acne and Rosacea
- Actinic Keratosis Basal Cell Carcinoma and other Malignant Lesions
- Seborrheic Keratoses and other Benign Tumors

It was created using React Native with Expo. The Tensorflow model shows an accuracy of around 55%. The application is now available only in Polish as it was created for the 61th. Conference of the AGH University of Science and Technology Student Research Groups so the repository also contains a presentation given there.

## Some UI screenshots:
![image](https://github.com/gredajustyna/Dermtektyw/assets/83274413/e58e5fd5-baeb-4260-9555-15386e9c104c)

## Usage:

https://github.com/gredajustyna/Dermtektyw/assets/83274413/f796f822-b8ba-44f8-ae54-7a57b81cabfd

## How to run
The application was developed using MacOS and iPhone and the instructions will also be guide to run on these platforms. 
- Clone the entire repository
- Move and unpack the `model` folder inside `/opt/homebrew/var/www` folder
- Make sure the Apache is installed on your device
- Edit the `/opt/homebrew/etc/httpd/httpd.conf` file and add the following code:
  ```
  LoadModule headers_module libexec/apache2/mod_headers.so
  <Directory "/opt/homebrew/var/www/model/">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
    Header set Access-Control-Allow-Origin "*"
    Header set Access-Control-Allow-Methods "GET, POST, OPTIONS"
    Header set Access-Control-Allow-Headers "Content-Type, Authorization"
  </Directory>
  ```
- Restart the apache server: `brew services restart httpd`
- The steps above describe just how to host the model on Apache server and allow CORS so that the model is shared in a proper format. Adjust them to your platform.
- Open the repository in a code editor like VS Code
- Run `npx expo` ih the terminal in the main directory
- Download the Expo Go app from AppStore
- Scan the QR code visible in the terminal to run the app
