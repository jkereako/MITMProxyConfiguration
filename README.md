# Configurations for mitmproxy
This script automatically sets and activates HTTP and HTTPS proxies on your
active network device and automatically deactivates the proxies when you kill
mitmproxy.

> **Only works with version 3.0 and later!** The 3.0 release had quite a few
> breaking changes.

# Installation
1. Clone the repository and copy the directory `.mitmproxy` to your home 
directory.

```sh
$> git clone git@github.com:jkereako/MITMProxyConfiguration.git
Cloning into 'MITMProxyConfiguration'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (5/5), done.
Receiving objects: 100% (5/5), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0

$> cp -R MITMProxyConfiguration/.mitmproxy ~/
```

2. Fire up mitmproxy.

*Installation of mitmproxy root certificates*

3. Navigate to `http://mitm.it` in your browser and select Apple.
4. Follow the instructions for how to install the certificate.

That's it! Now you can view traffic for the domains specified in `view_filter`.

# Files
### config.yaml
This is mitmproxy's config file which is loaded on start up.

### toggle_system_proxies.py
This script makes mitmproxy much easier to work with when using it on macOS. It
will automatically set and activate proxies on the network device you're
currently using. When you quit mitmproxy, the script will automatically
deactivate those proxies.

### error_response.py
This script allows you to test response time-outs and error responses in the
form of an HTTP status code or a custom error code your service may send back.
When provided arguments via the query string, this script will return a status
code, an error code encoded in JSON and a response delay.

Here are the supported query string parameters and the type of their arguments:

|          |  Parameter  |  Type     |
|-----------------|------|-----------|
| Status code     | `s`  |  Integer  |
| Error code      | `e`  |  String   |
| Response delay  | `d`  |  Integer  |

# mitmproxy script debugging
To debug a custom script in mitmproxy, use mitmdump.

```sh
 $> mitmdump -s custom_script.py
```

This runs mitmproxy directly in the command line which allows you to see errors
printed to stderr and logs printed to stdout.