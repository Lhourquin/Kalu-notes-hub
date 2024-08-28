# Prevent brute force attack

## Add limitation to request allowed

If we don't add limitation, a malicious actor could use multiple intput to stolle all db in few hours, and he can take all time he want to brute force an athentication for example.
So to add more safe layer, we need to add rate limit. By dot his, we make the task more difficult. But it's not enough, we need to add more protection.

## Don't send response to clear

That mean, the response in error case should not return a message that given to an attacks hint about how the code work, for instance if a wrong email is the athentication return specially that's authentication refused because the mail. that give to the malicious actor some hint to continue in the right way to found vulnerability.
So for example, if an authentication failed, we send the same response unclear, just for instance "unable-auth", "Unable to authenticate (Invalid email or password)" and the same status code, for example 404, intead of 404 for wrong email, and 401 for unauthorized because the mail is good but not the password.
This may seem counterintuitive for some people, and ask "but if we don't know how we can do ?" WE SHOULD NOT KNOW. We never give the reason of a failed authentication. We give the information of the authentication is failed, not more.

## Lock the account

If there are too many connection attempts, locking the account and notifying by email is a good practice, for example after 5 attempts, the account is locked and mail is sent to the user. And when the account is locked, we don't give this information, only the user of the account on this mail.
By the way, the malicious actor don't know if the account is locked, and even if he found the good password, he cannot cannect to the platform, because the account is locked. (redis ?)
