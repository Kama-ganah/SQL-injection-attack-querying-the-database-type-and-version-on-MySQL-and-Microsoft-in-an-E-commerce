# Overview
During testing of the product listing functionality, a high-severity SQL Injection vulnerability was identified in the category filter parameter. By manipulating this parameter, it was possible to inject UNION-based SQL payloads and retrieve backend database metadata, including the database type and version. The flaw affected both MySQL and Microsoft SQL Server backends, demonstrating insufficient input validation and unsafe query construction.

# Steps Undertaken

Step 1: Intercepted the product filter request containing the category parameter using Burp Suite.

Step 2: Injected UNION-based payloads to determine the number of columns returned by the original query.

Step 3: Confirmed two injectable columns capable of rendering text output.

Step 4: Used a UNION SELECT statement to extract the database version via the @@version variable.

Step 5: Verified the database technology and version information was reflected in the application response.

# Conclusion

This assessment confirmed a classic but critical SQL Injection vulnerability in the product category filter. The ability to enumerate database type and version indicates full query manipulation is possible, exposing the application to data extraction, modification, and potential full database compromise. Immediate remediation through parameterized queries and strict server-side input handling is required.
