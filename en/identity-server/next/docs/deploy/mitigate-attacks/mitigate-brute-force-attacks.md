# Mitigate Brute Force Attacks

The following sections describe the impact of a brute force attack and the approaches you can use to mitigate it.

## How can brute force attacks be harmful?

Brute force attacks are a popular mechanism for cracking passwords. It uses automated software to generate a large number of possible guesses to the value of the required data (in this case, to guess the password) and works by trial and error. A brute force cracking application proceeds through all possible combinations of legal characters in a sequence.
For example, several HTTP brute-force tools can relay requests through many different open proxy servers. As each of the requests appears to come from a different IP address, simply blocking the IP address will not work against these attacks.

## Mitigate brute force attacks

Setting up the system to prompt the password recovery process after a few failed attempts so that the user has to provide answers to secret questions, can mitigate this risk. However, similar to using these tools to guess a user's credentials, it can also be used to guess answers to secret questions. To further mitigate this attack, you can use the following approaches:

- Implement an account lockout mechanism that temporarily suspends user access after a predefined number of unsuccessful login attempts for a specified duration. For instructions on setting this up, see [User Account Locking and Account Disabling]({{base_path}}/guides/user-accounts/account-security/login-attempts-security/).

- Integrate a reCAPTCHA challenge into the login process following a designated threshold of failed login attempts. The reCAPTCHA serves as a security measure to distinguish between human users and automated scripts or bots, ensuring the system's integrity and security. For instructions on setting this up, see [Configure bot detection]({{base_path}}/guides/user-accounts/account-security/bot-detection/).
