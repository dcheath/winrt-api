---
-api-id: M:Windows.Security.Credentials.UI.UserConsentVerifier.CheckAvailabilityAsync
-api-type: winrt method
---

<!-- Method syntax
public Windows.Foundation.IAsyncOperation<Windows.Security.Credentials.UI.UserConsentVerifierAvailability> CheckAvailabilityAsync()
-->

# Windows.Security.Credentials.UI.UserConsentVerifier.CheckAvailabilityAsync

## -description
Checks to see whether a verifier device, such as a Microsoft Passport PIN, Windows Hello, or fingerprint reader, is available.

## -returns
A [UserConsentVerifierAvailability](userconsentverifieravailability.md) value that describes the result of the availability check operation.

## -remarks
The following example shows a method that checks to see if fingerprint authentication is supported for the current computer and returns a message that describes the result.



```csharp
public async Task<string> CheckConsentAvailability()
{
    string returnMessage = "";

    try
    {
        // Check the availability of Hello authentication.
        var ucvAvailability = Windows.Security.Credentials.UI.UserConsentVerifier.CheckAvailabilityAsync();

        switch (ucvAvailability)
        {
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.Available:
                returnMessage = "User consent verification available!";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.DeviceNotPresent:
                returnMessage = "No PIN found, please set one up.";
                break;
            default:
                returnMessage = "User consent verification is currently unavailable.";
                break;
        }
    }
    catch (Exception ex)
    {
        returnMessage = "User consent verification failed: " + ex.ToString();
    }

    return returnMessage;
}
```

```javascript
function checkConsentAvailability() {
    try {
        // Check the availability of Hello authentication.

        Windows.Security.Credentials.UI.UserConsentVerifier.checkAvailabilityAsync().then(
        function (ucvAvailability) {

            switch (ucvAvailability)
            {
                case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.available:
                    outputDiv.innerHTML = "<br/>User consent verification available!";
                    break;
                case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.deviceNotPresent:
                    outputDiv.innerHTML = "<br/>No PIN found, please set one up.";
                    break;
                default:
                    outputDiv.innerHTML = "<br/>User consent verification is currently unavailable.";
                    break;
            }
        });
    }
    catch (ex) {
        outputDiv.innerHTML = "<br/>User consent verification failed: " + ex.toString();
    }
}
```



## -examples

## -see-also
[Fingerprint biometrics](http://msdn.microsoft.com/library/55483729-5f8a-401a-8072-3cd611ddfed2), [UserConsentVerifier sample](http://go.microsoft.com/fwlink/p/?LinkID=303650), [Windows.Security.Credentials.UI](windows_security_credentials_ui.md), [Authentication and user identity](http://msdn.microsoft.com/library/53e36ddc-200a-4850-aaf0-07eca3662bb9)