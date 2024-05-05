# FFUF basics

## Using ffuf to Fuzz a File Upload Form with Different PHP Extensions

**I. Setting Up the Target:**

1. **Identify the target URL:** Locate the web page containing the file upload form.
2. **Analyze the form:** Inspect the HTML code to find the following elements:
 - The form's action attribute (specifies where the form data is submitted).
 - The name of the file input field.
 - Any restrictions or validations on file types.

**II. Crafting the FUZZ Payload:**

1. **Create the payload file:**
 - Create a text file (e.g., `payloads.txt`) containing the file extensions you want to try, each on a separate line. For example:
 ```
 php
 php3
 phtml
 inc
 ```
2. **Utilize ffuf commands:**
 - Replace the placeholders below with your specific information:
 - `TARGET_URL`: The action URL of the file upload form.
 - `FILE_FIELD`: The name of the file input field.
 - `PAYLOADS_FILE`: The path to your payloads file (`payloads.txt`).

**Command:**

```
ffuf -u TARGET_URL -w PAYLOADS_FILE -H \"Content-Type: multipart/form-data; boundary=--------------------------168372996359978745573820585509\" -X POST -d \"--------------------------168372996359978745573820585509\r\nContent-Disposition: form-data; name=\\"FILE_FIELD\\"; filename=\\"payload.FUZZ\\"\r\nContent-Type: application/x-php\r\n\r\nFUZZ\" -mc 200
```

**Explanation:**

- `-u`: Specifies the target URL.
- `-w`: Provides the payloads list file.
- `-H`: Sets the Content-Type header for multipart/form-data with a boundary string.
- `-X`: Sets the request method to POST for uploading files.
- `-d`: Defines the request body with the appropriate HTML structure, form field name (`FILE_FIELD`), placeholder for the extension (`FUZZ`), and file type (`application/x-php`).
- `-mc 200`: Filters results to display only responses with HTTP code 200 (potentially successful uploads).


**III. Running the Command and Analyzing Results:**

1. Execute the `ffuf` command from your terminal.
2. ffuf will start sending requests, testing different PHP extensions from the provided payloads file.
3. Monitor the output for responses with HTTP code 200 and check the server's responses to identify potential vulnerabilities related to the extension tested.


**IV. Important Notes:**

- This example is for demonstration purposes only. Utilize ffuf responsibly and avoid any illegal activities.
- Ensure you have permission to test the target website before initiating any requests.
- Adapt the command to fit the specific target form and validation rules.
- Modify the file types and payloads based on the form's expected behavior.

**V. Disclaimer:**

This information is for educational purposes only. I am not responsible for any consequences resulting from misuse or illegal activities using ffuf. Always exercise ethical judgment and follow all applicable laws.

## Using ffuf to fuzz a form with a 'file' field for PHP extensions

Here's an example of how you can use ffuf to fuzz a form with a 'file' field that allows uploading PHP files and test different extensions:

**1. Setting up the command:**

```
ffuf -u \"https://example.com/upload\" -w wordlist.txt -H \"Content-Type: multipart/form-data\" -d \"file=@FUZZ\" -D \"FUZZ:0\" -t 100
```

**Explanation of the options:**

* `-u`: This specifies the URL of the form you want to fuzz.
* `-w wordlist.txt`: This specifies the wordlist containing the PHP extensions you want to test (e.g., \"php\", \"phtml\", \"php3\").
* `-H`: This sets the HTTP header for the request. Here, we set it to \"Content-Type: multipart/form-data\" as most file upload forms use this content type.
* `-d`: This specifies the data to be sent with the POST request. Here, we use \"@FUZZ\" to denote the file field and substitute it with the extensions from the wordlist.
* `-D`: This defines a custom variable named \"FUZZ\". The value of the variable will be taken from the current line of the wordlist.
* `-t`: This specifies the number of threads to use for sending requests. You can adjust this value based on your system resources and desired speed.

**2. Preparing the wordlist:**

Create a file named `wordlist.txt` and add the list of PHP extensions you want to test, one extension per line. For example:

```
php
phtml
php3
```

**3. Running the command:**

Save the command above in a file named `fuzz.sh` and make it executable using `chmod +x fuzz.sh`. Then, run the command:

```
./fuzz.sh
```

This will start sending requests to the form with the different extensions from the wordlist.

**4. Analyzing the results:**

ffuf will display the status code of each request. If the server returns a 200 status code for a specific extension, it indicates that the extension might be allowed. You can then investigate further by trying to upload a malicious PHP file with that extension.

**Additional notes:**

* This is a basic example, and you can customize the command further by adding additional options and filters.
* Be sure to test on a safe environment before attempting this on a live website.
* Do not use this technique for malicious purposes.

Here are some resources that you might find helpful:

* **ffuf documentation:** https://ffuf.readthedocs.io/en/latest/
* **Testing file upload vulnerabilities with ffuf:** https://github.com/ffuf/ffuf/wiki/Testing-file-upload-vulnerabilities
* **Hunting for File Upload Vulnerabilities with ffuf:** https://pentest.medsec.co.uk/hunting-for-file-upload-vulnerabilities-with-ffuf/

I hope this helps! Let me know if you have any other questions.