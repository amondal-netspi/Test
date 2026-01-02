# Demonstration of how SRI works
This is a small demo designed to show how SRI (Subresource Integrity) checks work and how they are related to Cross-Domain Script Includes. 

Read all about Subresource Integrity here: [Subresource_Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Subresource_Integrity)

### Example 1 - A web page includes a Cross-Domain JavaScript file (main.js) and verifies the integrity of the file with SRI:

- Navigate to [safe-cross-origin.html](safe-cross-origin.html) and check the [source code](https://raw.githubusercontent.com/amondal-netspi/Test/refs/heads/main/SRI/safe-cross-origin.html) of the page.
- Observe that the ***main.js*** file is loaded from a third-party domain, and a sha384 hash of the included script file is added via the ***integrity*** attribute.
- Click on the ***Click-Me*** button to verify that the script has been loaded successfully.

### Example 2 - A web page includes a Cross-Domain JavaScript file (main2.js) and verifies the integrity of the file with SRI. However, this time, the content of the remote JavaScript file has been altered to include malicious code:

- Navigate to [safe-cross-origin-2.html](safe-cross-origin-2.html).
- Click on the ***Click-Me*** button again. Observe that nothing happens this time, as the script was not loaded.
- Check the browser's console and observe the error that is being thrown. Observe that the hash mentioned in the error does not match the one mentioned in the ***integrity*** attribute. As a result, the script was prevented from being loaded and executed in the application's context.

### Example 3 - A web page includes a Cross-Domain JavaScript file (main2.js) without verifying the integrity of the file using SRI. The content of the remote JavaScript file has been altered to include malicious code:
- Navigate to [unsafe-cross-origin.html](unsafe-cross-origin.html) and check the [source code](https://raw.githubusercontent.com/amondal-netspi/Test/refs/heads/main/SRI/unsafe-cross-origin.html) of the page.
- Observe that the ***main2.js*** file is loaded from a third-party domain, and no ***integrity*** attribute has been included in the <script> tag.
- Click on the ***Click-Me*** button and observe that the malicious script is loaded and executed successfully.
