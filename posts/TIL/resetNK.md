# Resetting Nitrokey Pro 2 User/Admin Pin

###### [Home](https://eduardo-granados.github.io/)

---


### notes



At some point I reset my user pin `123456` and admin pin `12345678` from their defaults to something else which I forgot. Thanfully I haven't used my Nitrokey 


3 main commands are `gpg --card-edit`, followed by `admin` and finally: `factory-reset`

The following table describes the factory reset operation:

| Property | Nitrokey Factory Reset |
| - | - |
| Requires admin PIN | Yes |
| Destroys OpenPGP keys | Yes |
| Destroys Password Safe | Yes |
| Destroys One-Time Passwords | Yes |
| Destroys Encrypted Volume | Yes |

Nitro actual page on how to factory reset `https://docs.nitrokey.com/storage/windows/factory-reset#:~:text=The%20factory%20reset%20can%20be,Special%20Configure%2D%3EFactory%20reset%20.&text=The%20factory%20reset%20is%20an,with%20the%20parameter%20%2D%2Dadmin%20.&text=Clears%20the%20encryption%20key%20without%20overwriting%20the%20encrypted%20data.`

nitro support link with visual guide to factory reset `https://support.nitrokey.com/t/reset-admin-pin/871/2`