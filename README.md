# TextLink python client

[![PyPI](https://img.shields.io/pypi/v/textlink.svg)](https://pypi.python.org/pypi/textlink)
[![PyPI](https://img.shields.io/pypi/pyversions/textlink.svg)](https://pypi.python.org/pypi/textlink)

### Supported Python Versions

This library supports the following Python implementations:

* Python 3.6
* Python 3.7
* Python 3.8
* Python 3.9
* Python 3.10
* Python 3.11
* Python 3.12

## Installation
`pip install textlink`

## Sending an SMS

To send an SMS, you have to create an API key using the [TextLink dashboard](https://textlinksms.com/dashboard/api). When you register an account, you automatically get an API key with one free SMS which you can send anywhere.

### Just send a message

```python
import textlinksms as tl
tl.useKey("YOUR_API_KEY")

tl.sendSMS("+381611231234", "Dummy message text...")
```

### Handle response

```python
result = tl.sendSMS("+381611231234", "Dummy message text...")
if(result.ok):
  print(result.data)
else:
  print(result.message)
```

### Example result object of the successfully sent message

```json
{
    "ok": true
}
```

### Example result object of the unsuccessfully sent message

```json
{
    "ok": false,
    "message": "API key not found"
}
```

## Verifying a phone number

You can also use our service to easily verify a phone number, without storing data about the phones that you are about to verify, because we can do it for you.

### Example usage

```python
# User has sent his phone number for verification
resultSMS = tl.sendVerificationSMS ("+11234567890", service_name, expiration_time, source_country)

# Show him the code submission form
# We will handle the verification code ourselves

# The user has submitted the code
resultCode = tl.verifyCode("+11234567890", user_entered_code)
# if `resultCode.valid` is True, then the phone number is verified. 
```

#### Verification options (Optional)

`service_name` is what the user will see in the verification message, e. g. `"Your verification code for Guest is: CODE"`

`expiration_time` is how many miliseconds the code is valid. Default is 10 minutes.

`source_country` is the ISO-2 code of the sender's phone number country.

## Getting help

If you need help installing or using the library, please check the [FAQ](https://textlinksms.com) first, and contact us at [help@textlinksms.com](mailto://help@textlinksms.com) if you don't find an answer to your question.

If you've found a bug in the API, package or would like new features added, you are also free to contact us!
