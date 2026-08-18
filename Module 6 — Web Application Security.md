# 1. Module Overview

Module 6 mainly focuses on:

* Web application security
* Insecure coding practices
* Authentication and session weaknesses
* Input validation
* Techniques attackers use to exploit web applications

## Main Idea

A secure application is not only about finding vulnerabilities after development.
Security should be built into the application from the beginning.
This is called:

> **Shift-Left Security**

---

# 2. Shift-Left Security

Shift-left security means introducing security practices early in the software development lifecycle, rather than waiting until the application is finished.

## Example

```text
Developer writes code
        ↓
Code is committed
        ↓
Automated security scanner checks it
        ↓
Developer fixes vulnerabilities
Why It MattersWhen developers receive security feedback during development:Vulnerabilities can be fixed earlier.Fixing bugs is generally easier.Developers learn from their mistakes.The same insecure coding practices are less likely to be repeated.3. Insecure Coding PracticesInsecure coding can introduce vulnerabilities that attackers may exploit.Important examples include:Sensitive information in source-code commentsPoor error handlingHard-coded credentialsRace conditionsUnprotected APIsHidden form fieldsLack of code signing4. Sensitive Information in CommentsDevelopers sometimes leave sensitive information inside source-code comments.ExampleJavaScript// Database password: admin123
// API key: ABC123...
// Temporary admin account: testadmin
An attacker who obtains the source code may discover these secrets.Security IssueCWE-615 — Information Exposure Through CommentsComments Should Never ContainPasswordsAPI keysAuthentication tokensPrivate keysInternal secrets5. Improper / Verbose Error HandlingApplications sometimes display too much information when an error occurs.Dangerous Error Information Can IncludeError codesDatabase errorsSQL statementsStack tracesFile pathsSoftware versionsInternal configuration detailsThis information can help attackers understand the application's internal structure and identify additional attack opportunities.ExampleInstead of:PlaintextSQL Error: MySQL syntax error near users.php line 42
A safer application might display:PlaintextAn unexpected error occurred. Please try again later.
Detailed diagnostic information should be available to developers/support staff, but should not be exposed to attackers.6. Hard-Coded CredentialsHard-coded credentials are usernames, passwords, API keys, or other secrets directly embedded in application code.ExamplePythonusername = "admin"
password = "Password123"
This is extremely dangerous because anyone who obtains the source code may obtain the credentials.CWECWE-798 — Use of Hard-coded CredentialsPossible ImpactHard-coded credentials may allow an attacker to:Access the applicationAccess databasesAccess serversAccess APIsCompletely compromise systemsBetter ApproachUse secure:Secret management systemsEnvironment variablesCredential vaultsKey-management systems7. Race ConditionsA race condition occurs when two or more operations happen close together or simultaneously, but the application requires them to happen in a specific order.An attacker may exploit a small timing window between a security check and the actual operation.TOCTOURace conditions are commonly associated with:Time-of-Check to Time-of-Use (TOCTOU)Simple ExampleImagine an application:Checks whether an account has enough money.Performs the withdrawal.If an attacker can trigger multiple withdrawals between these operations, the application might incorrectly allow more money to be withdrawn than should be possible.Important: Race-condition attacks are generally difficult to exploit because precise timing is often required.8. APIsAPI = Application Programming InterfaceAPIs allow applications and systems to communicate with each other.Modern applications heavily rely on APIs.ExamplesMobile applications communicating with serversWebsites communicating with backend servicesOnline dashboardsPayment systemsCloud services9. Major API TechnologiesSOAPSOAP = Simple Object Access ProtocolCharacteristics:Standards-based web-services protocolOriginally developed by MicrosoftUses XMLHas a strict messaging structureCommonly found in older/legacy applicationsRESTREST = Representational State TransferCharacteristics:Generally easier to use than SOAPCommonly uses JSONUses HTTPCommonly documented with:SwaggerOpenAPI SpecificationREST APIs are extremely common in modern web applications.GraphQLGraphQL is a query language for APIs.It is commonly used by:Mobile applicationsWeb applicationsOnline dashboardsEasy MemoryPlaintextSOAP     → XML
REST     → JSON + HTTP
GraphQL  → Query Language
10. SOAP vs REST vs GraphQLTechnologyMain CharacteristicSOAPXML-based web-services protocolRESTAPI style commonly using JSON and HTTPGraphQLQuery language for APIs11. HTTPS and TLSAPIs should use HTTPS rather than plain HTTP.HTTPSHTTPS is the secure version of HTTP.It uses TLS (Transport Layer Security) to encrypt communication.This helps protect sensitive information while it travels between the client and server.12. API DocumentationAPI documentation can reveal how an application works.For a penetration tester, API documentation can provide valuable information about:EndpointsParametersRequestsData structuresAuthenticationAvailable functionalityAPI Documentation FormatsImportant API documentation formats include:Swagger / OpenAPIUsed for documenting, designing, and developing APIs.WSDLWSDL = Web Services Description LanguageXML-basedUsed to describe web servicesWADLWADL = Web Application Description LanguageXML-basedUsed to describe web applications13. API Testing During Penetration TestingWhen testing an API, capture the complete HTTP request, not just the URL.Tools such as:Burp SuiteOWASP ZAPcan work as web proxies and capture HTTP requests.Look ForUnusual parametersAbnormal HTTP headersIDs in URLsNumbers that change between requestsDatesJSON parametersXML parametersOther structured valuesThese can provide clues about how the API processes data.14. API Parameter EnumerationSuppose you observe URLs such as:HTTP/s/abcd/page
/s/dead/page
/s/beef/page
The changing values:Plaintextabcd
dead
beef
may represent an API parameter rather than an actual directory.Identifying changing parameters can help penetration testers understand how an application handles requests and resources.15. API FuzzingFuzzing is an automated testing technique that sends unexpected, malformed, or unusual input to an application.Goals of FuzzingFuzzing can help identify:Application crashesInput-validation problemsUnexpected behaviorSecurity vulnerabilitiesExample InputsA tester may send:Very large valuesSpecial charactersUnicode charactersInvalid data typesUnexpected parametersThe tester then observes how the application responds.16. RadamsaRadamsa is a fuzzing tool that generates modified or malformed test data.It can be used to test:ApplicationsProtocolsParametersIts purpose is to generate unusual input that can reveal unexpected application behavior.17. API Security Best Practices1. Use HTTPSUse HTTPS with strong and properly configured TLS.2. Validate ParametersApplications should verify that incoming parameters contain valid and expected data.3. Sanitize InputInput should be handled safely before being processed or used.4. Detect Attack PatternsApplications should monitor for common attack patterns and malicious input.5. Use Strong AuthenticationUse appropriate authentication mechanisms to verify users and systems.6. Use Strong AuthorizationUsers should only be able to access resources they are authorized to access.7. Use Reputable LibrariesUse trusted and well-maintained libraries instead of unnecessarily creating security-sensitive functionality from scratch.8. Separate API Security from Application LogicSecurity controls can be implemented in a separate security layer or tier where appropriate.9. Identify Sensitive DataOrganizations should know which information is:PublicInternalSensitiveConfidentialSensitive information should receive appropriate protection.10. Perform Security ReviewsWhenever possible, security professionals should review API implementations and security controls.18. Hidden ElementsWeb applications may contain hidden HTML form fields.ExampleHTML<input type="hidden" name="price" value="100.00">
Although the field is not normally visible to the user, its value is still sent to the server.An attacker may modify the value.ExampleOriginal:Plaintextprice=100
Modified:Plaintextprice=1
If the server blindly trusts this value, the application may be vulnerable to parameter tampering.Important: Hidden does NOT mean secure.The server must independently validate important values rather than trusting values supplied by the client.Hidden fields can have legitimate purposes, including certain CSRF-related mechanisms, so a hidden field is not automatically a vulnerability.19. Code SigningCode signing uses a digital signature to verify that software:Comes from the expected developer or source.Has not been modified after signing.It involves:Private keysPublic keysDigital signaturesTrusted certificate authorities, where applicableBasic ProcessPlaintextDeveloper:
Software → Sign with Private Key

System/User:
Software → Verify Signature with Public Key
If the software is modified after it was signed, signature verification may fail.20. Subresource Integrity (SRI)SRI = Subresource IntegritySRI allows a web page to specify a cryptographic hash for an external resource.The browser can then verify that the downloaded resource matches the expected hash.PurposeSRI helps protect against modification or tampering of external resources such as:JavaScript filesOther externally loaded resourcesBasic IdeaPlaintextExpected Hash
      ↓
Downloaded Resource
      ↓
Hash Comparison
      ↓
Match → Resource accepted
Mismatch → Resource rejected
21. Web ProxiesA web proxy can sit between a browser and a web application:PlaintextBrowser ↔ Proxy ↔ Web Application
A penetration tester can use a proxy to:Intercept requestsInspect requestsModify requestsForward requestsAnalyze responsesWeb proxies are extremely useful during web application penetration testing.22. Burp SuiteBurp Suite is a popular web application security testing platform.It includes a web proxy that can intercept HTTP/HTTPS traffic.EditionsCommunity EditionProfessional EditionCommon UsesBurp Suite can be used for:Intercepting requestsModifying parametersExamining cookiesTesting authenticationTesting authorizationAnalyzing application behavior23. OWASP ZAPOWASP ZAP = Zed Attack ProxyOWASP ZAP is a free and open-source web application security testing tool.It provides features such as:Web proxyAutomated scanningFuzzingVulnerability detectionZAP can help security testers identify and investigate vulnerabilities in web applications.24. Burp Suite vs OWASP ZAPFeatureBurp SuiteOWASP ZAPWeb proxy✅✅Intercept traffic✅✅Modify requests✅✅Automated scanning✅✅Fuzzing✅✅Free versionCommunity EditionFree/Open SourcePractice QuestionWhich tools can be used to intercept and forward web traffic?Burp SuiteOWASP ZAP25. Directory and File Enumeration ToolsThese tools help discover files and directories on web servers.GobusterWritten in GoUsed for directory and file enumerationUses wordlistsFFUFWritten in GoA fast web fuzzerCan be used for web enumeration and fuzzingFeroxbusterWritten in RustUsed for web reconnaissance and fuzzingDirBusterUsed to discover directories and files on web servers.26. WordlistsEnumeration tools commonly use wordlists.A wordlist is a file containing many possible values that a tool can test.ExamplePlaintextadmin
login
dashboard
backup
uploads
api
config
The tool can use these values to test whether corresponding resources exist on the target.27. OWASP WSTGOWASP WSTG = OWASP Web Security Testing GuideIt is an important resource for web application security testing.It provides guidance on:Web application security testingVulnerability identificationTesting methodologiesSecurity recommendationsVulnerability mitigationFor penetration testers, the WSTG is an important reference when conducting web application security assessments.28. ZAP + WSTGThe module demonstrates combining:PlaintextOWASP WSTG → Methodology and Reference
        +
OWASP ZAP → Practical Scanning and Testing
Together, they can help testers:Identify potential vulnerabilities.Investigate findings.Understand the vulnerability.Determine the underlying cause.Identify appropriate mitigation guidance.29. Important Vulnerability ConceptsInformation ExposureSensitive information is accidentally exposed to unauthorized users.Improper Error HandlingApplication errors reveal information that could help attackers.Hard-Coded CredentialsCredentials are directly embedded into application source code.Race ConditionAn attacker exploits timing or an incorrect sequence between operations.API Security IssuesAPIs lack adequate:AuthenticationAuthorizationInput validationOther necessary security controlsParameter TamperingAn attacker modifies application parameters to change application behavior.Lack of Code SigningThe authenticity and integrity of software cannot be reliably verified.30. Important CWE NumbersCWEVulnerabilityCWE-615Information Exposure Through CommentsCWE-798Use of Hard-coded CredentialsCWE-227API Abuse31. Tools to RememberToolMain PurposeBurp SuiteWeb proxy and security testingOWASP ZAPProxy, scanning, and fuzzingGobusterDirectory/file enumerationFFUFFast web fuzzingFeroxbusterWeb reconnaissance/fuzzingDirBusterDirectory enumerationRadamsaFuzzing/test-data generation32. High-Value ConceptsShift LeftSecurity testing should begin early in the software development lifecycle.Hidden ≠ SecureA hidden HTML field can still be modified by the client.Error MessagesDetailed error messages can reveal useful information to attackers.Hard-Coded CredentialsPasswords, API keys, and other secrets should not be directly embedded in source code.Race ConditionThink:Timing + Incorrect Sequence + Small Exploitation WindowAPI TestingDo not inspect only URLs. Capture and analyze the complete HTTP requests.FuzzingThink:PlaintextAutomated unusual/malformed input
              ↓
Observe application behavior
Code SigningThink:PlaintextDigital Signature
       ↓
Authenticity + Integrity
SRIThink:PlaintextCryptographic Hash
       ↓
Verify External Resource Integrity
Web ProxyThink:PlaintextBrowser → Proxy → Server
A proxy allows security testers to intercept, inspect, and modify HTTP/HTTPS traffic.
