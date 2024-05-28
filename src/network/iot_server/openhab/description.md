# OpenHAB IoT Server
## Opening OpenHAB IoT Server

Here's how to open OpenHAB IoT server, with specific steps depending on your platform:

**1. Open a Web Browser:**

Open any web browser you like, like Chrome, Firefox, or Safari.

**2. Type the OpenHAB URL in the Address Bar:**

The address will usually be:

* `http://openhab:8080/` for a local installation, where \"openhab\" is the hostname or IP address of your server.
* The URL provided to you if your OpenHAB is hosted online.

**3. Log in to the OpenHAB Interface:**

You will likely encounter a login prompt. Enter the default login credentials:

* **User Name:** `admin`
* **Password:** `habopen`

**4. Accessing Different Interfaces:**

Once logged in, you can access various OpenHAB interfaces:

* **Main UI (Paper UI):** This is the user interface for managing items, things, rules, and other OpenHAB elements.
* **HabPanel**: A user interface designed for touchscreens and mobile devices.
* **Basic UI:** A stripped-down interface for simple control and monitoring, useful on devices with limited resources.

**5. Additional Notes:**

* If the default URL or credentials do not work, check OpenHAB's documentation or community forums for troubleshooting steps.
* For secure communication, access OpenHAB through `https://` instead of `http://`, assuming your server has a valid SSL certificate.
* You can configure OpenHAB to use a custom port instead of the default 8080. The correct URL will then include your chosen port number.

**6. Platforms Specific:**

* **OpenHABian (Raspberry Pi):** Open the web browser on your Raspberry Pi or a device connected to the same network. Type the address `http://openhabianpi:8080`.
* **Windows/Mac:** Open a web browser and type the OpenHAB server IP address followed by `:8080`, for example, `http://192.168.1.100:8080`.
* **Synology:** Open the OpenHAB Control Panel in the Synology Package Center. Go to the \"Web UI\" tab and click the \"Open\" button.
* **Docker:** If running OpenHAB in a Docker container, you may need to use the container IP or hostname, and port number specified when starting the container.

**7. Additional Resources:**

* OpenHAB Documentation: https://www.openhab.org/docs/
* OpenHAB Forum: https://community.openhab.org/
* OpenHAB Paper UI Tutorial: https://www.openhab.org/docs/tutorial/paperui.html

**8. Safety Considerations:**

Remember to update the OpenHAB software regularly to ensure security, as vulnerabilities can be found and exploited. Be cautious when installing untrusted add-ons or plugins to avoid potential harm to your system.

Please let me know if you have any further questions or need more assistance.
