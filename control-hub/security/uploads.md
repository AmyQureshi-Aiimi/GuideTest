# Uploads

## File Scanner Configurator

1. Drag the scanner type you would like to use into the right box.

### File Type Scanner

1. There are no further configurations needed for this scanner.

### Local File Scanner

1. **Working Directory** - Enter the working directory that should be used.&#x20;
   * By default this is set to Path.GetTempPath()
2. **Wait Time** - Enter how many seconds to wait for the local AV to Kick in.
   * This only applies to on non-Windows Operating Systems.
   * By default this is set to 1 second.

### Test File Scanner

1. **Test Signatures** - Enter the signatures that should that should be tested for. The first 256 bytes of each provided file will be converted to unicode. These are then compared against the test signatures. If a match is found then the plugin will behave as if a malicious file was detected.

<figure><img src="../../.gitbook/assets/image (140).png" alt="" width="563"><figcaption></figcaption></figure>
