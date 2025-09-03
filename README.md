Personal Password Manager
A secure, web-based password manager that uses end-to-end encryption to store your sensitive credentials. 
This application is built with HTML and JavaScript, and it uses Firebase for authentication and database services. 
All encryption and decryption happen on your device, ensuring that only you can access your passwords.

#Key Features
1. End-to-End Encryption: Your data is encrypted with a Master Password that only you know. This key is never stored, providing maximum security.

2. Secure Authentication: Log in with your unique email and password.

3. Two-Factor Authentication (2FA): A 4-digit PIN is required for quick and secure access after unlocking the vault.

4. Full CRUD Functionality: Easily Create, Read, Update, and Delete your password entries.

5. Strong Password Generator: Create strong, unique passwords with customizable length and character types.

6. Quick Search & Copy: Instantly search your vault and copy passwords to your clipboard.

7. Self-Contained: The entire application runs from a single HTML file.

#How It Works (Security Model)
1. Login Password: This password authenticates you with Firebase and proves you own the account.

2. Master Password: This is the most critical password. It is never stored anywhere. It is used directly on your device to encrypt your data before sending it to the database and to decrypt it after fetching it. If you forget this password, your data is unrecoverable.

3. 2FA PIN: For added security, a PIN is used to access the unlocked vault. This PIN is itself encrypted by your Master Password before being stored.

#Setup and Installation Guide
Follow these steps to get the password manager running on your local machine.

1. Set Up Your Firebase Project
Go to the Firebase Console and create a new project.

2. Enable Authentication:
In your project, go to Authentication > Sign-in method.
Click on Email/Password and Enable it.

3. Enable Realtime Database:
Go to Realtime Database > Create Database.
Choose a location and select Start in test mode. Click Enable.

4. Get Your Firebase Configuration
In your Firebase project settings (click the gear icon ⚙️), scroll down to the "Your apps" section.
Click Add app and select the Web icon (</>).
Give your app a nickname and click Register app.
You will be shown your firebaseConfig object. Copy this entire object.

5. Configure and run the index.html file

#Usage Guide
1. Create Your Account (One-Time Step)
Since the public sign-up option has been removed for security, you need to create your account using the browser's developer console.

With the app running, right-click on the login page and select "Inspect" > "Console".

Paste the following command into the console, replacing the example email and password with your own.
// Make sure to import createUserWithEmailAndPassword in the main script.
createUserWithEmailAndPassword(auth, 'you@example.com', 'your-secure-password')
  .then((userCredential) => {
    // This part runs if the account is created successfully.
    const user = userCredential.user;
    console.log('Successfully created user:', user.email);
    alert('SUCCESS! Your account has been created. You can now log in.');
  })
  .catch((error) => {
    // This part runs if there was an error.
    console.error('Error creating user:', error.message);
    alert(`Error: ${error.message}`);
  });

// The main script has signInWithEmailAndPassword, but not createUser. For a one-time setup, you might need to temporarily
// add `createUserWithEmailAndPassword` to the import list in the script.

For a simpler setup, manually add a user in the Firebase Console:
Go to Authentication > Users > Add user.
Enter your desired email and password. This is the most reliable way to create your initial user.

2. First-Time Login
Enter the email and password you just created.
You will be prompted to enter a Master Password. Choose a strong, memorable password. Do not forget this password.
Next, you will be prompted to set up your 4-digit 2FA PIN.

3. Daily Use
Login: Use your email and password.
Unlock Vault: Enter your Master Password.

Access: Enter your 4-digit PIN.

Manage Passwords: Use the "Add Password" button to save new credentials. Click on existing entries to edit, delete, or copy the password.
