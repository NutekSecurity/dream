# Finding stack buffer overflows

https://stackoverflow.com/a/29902473

There are two main approaches for finding stack buffer overflows:

Black box testing The key to testing an application for stack overflow vulnerabilities is supplying overly large input data as compared to what is expected. However, subjecting the application to arbitrarily large data is not sufficient. It becomes necessary to inspect the application’s execution flow and responses to ascertain whether an overflow has actually been triggered or not. Therefore, the steps required to locate and validate stack overflows would be to attach a debugger to the target application or process, generate malformed input for the application, subject the application to malformed input, and inspect responses in a debugger. The debugger allows the tester to view the execution flow and the state of the registers when the vulnerability gets triggered

Gray Box Testing Manually review the code (disassemble it). When reviewing code for stack overflows, it is advisable to search for calls to insecure library functions like gets(), strcpy(), strcat() etc which do not validate the length of source strings and blindly copy data into fixed size buffers. Apart from manually reviewing code for stack overflows, static code analysis tools can also be of great assistance. Although they tend to generate a lot of false positives and would barely be able to locate a small portion of defects, they certainly help in reducing the overhead associated with finding low hanging fruits, like strcpy() and sprintf() bugs. A variety of tools like RATS, Flawfinder and ITS4 are available for analyzing C-style languages.

The best tools for those testings are: OllyDbg and IDA Pro (for static and dynamic debugging).
