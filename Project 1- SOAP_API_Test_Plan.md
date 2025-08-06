Test Plan for the DataFlex  Web Services for Testing ISBN Numbers
________________________________________
✅ Test Plan: SOAP API -IsValidISBN10
________________________________________
📝 1. Overview
This test plan is designed to test the IsValidISBN10 operation provided by the DataFlex SOAP Web Service hosted at:
https://webservices.daehosting.com/services/isbnservice.wso
The service takes a 10-digit ISBN (International Standard Book Number) as input and returns a boolean response indicating whether it is a valid ISBN-10 format or not.
________________________________________
📌 2. Objectives
•	Verify that the IsValidISBN10 service correctly validates 10-digit ISBN numbers.
•	Validate both valid and invalid ISBN inputs.
•	Test the service using different protocols (SOAP 1.1, SOAP 1.2, JSON).
•	Ensure that response is as expected across all input types and edge cases.
•	Validate service behavior under incorrect/malformed requests.
________________________________________
📬 3. Request Details
✅ Endpoint:
POST https://webservices.daehosting.com/services/isbnservice.wso
✅ SOAP Operation:
IsValidISBN10
✅ Parameter:
Parameter	Type	Description
sISBN	String	ISBN-10 input (e.g. 10 digits or 9 digits + X)
________________________________________
📦 4. Request Formats
✅ SOAP 1.1 Example:
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <IsValidISBN10 xmlns="http://webservices.daehosting.com/ISBN">
      <sISBN>0123456789</sISBN>
    </IsValidISBN10>
  </soap:Body>
</soap:Envelope>
✅ JSON Example:
{
  "sISBN": "0123456789"
}
________________________________________
✅ 5. Test Scenarios / Test Cases
TC#	Test Scenario	Input	Expected Output
TC01	Valid ISBN (10 digits)	"0471958697"	true
TC02	Valid ISBN (ends with 'X')	"030640615X"	true
TC03	Invalid ISBN (random digits)	"1234567890"	false
TC04	Invalid ISBN (too short)	"12345"	false
TC05	Invalid ISBN (11 digits)	"12345678901"	false
TC06	Invalid ISBN (contains special chars)	"12@#56789X"	false or error
TC07	Empty String	""	false or error
TC08	Null Input	null	error/exception
TC09	JSON request	JSON with valid ISBN	true
TC10	SOAP 1.2 request	Same as SOAP 1.1	true
TC11	HTTP GET (invalid method)	GET instead of POST	HTTP 405/500
TC12	High volume test (load test)	Multiple valid ISBNs	consistent true
TC13	Malformed XML in SOAP body	Broken envelope	500/Internal Error
________________________________________

🧪 6. Testing Types Covered
•	✔️ Functional Testing
•	✔️ Negative Testing
•	✔️ Boundary Testing
•	✔️ Security (Injection/Encoding)
•	✔️ Protocol Compatibility (SOAP 1.1, 1.2, JSON)
•	✔️ Load Testing (optional via Postman / JMeter)
________________________________________
🧰 7. Tools Required
•	Postman or SOAP UI (for manual API testing)
•	JMeter (for performance/load test)
•	JUnit/TestNG + RestAssured (for automation testing – optional)
•	Charles Proxy (to monitor raw HTTP calls – optional)
________________________________________
📂 8. Test Data (Sample Inputs)
Type	Value
Valid	0471958697
Valid	030640615X
Invalid	1234567890
Invalid	"" (empty)
Invalid	null
Invalid	12@#56789X
________________________________________
📤 9. Response Validation
•	HTTP Status Code: 200 OK for valid requests
•	Content-Type: text/xml or application/soap+xml
•	Response Body: Should include the <IsValidISBN10Result> boolean node
•	Error Handling: Server should handle invalid input gracefully
________________________________________

🔐 10. Security Considerations
•	Ensure the API does not expose internal logic or stack traces
•	Validate proper error codes for malformed or missing inputs
•	Confirm that excessive calls are rate-limited (optional)
________________________________________
📈 11. Test Execution & Reporting
•	All test cases will be documented with:
o	✅ Test Steps
o	✅ Expected Result
o	✅ Actual Result
o	✅ Pass/Fail Status
•	A test summary report will be created after execution
________________________________________
🧩 12. Automation Plan (Optional)
If automation is to be included:
•	Create a TestNG framework using REST-assured or Apache HTTP client for SOAP
•	Parameterize input data
•	Validate against expected boolean output and status code
•	Generate reports via Allure or Extent Reports
________________________________________
✅ Summary
This test plan provides full functional and structural coverage for the IsValidISBN10 SOAP Web Service and can be extended further as the system scales.
________________________________________

