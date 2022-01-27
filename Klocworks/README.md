# Klocwork 
---

_Required skills_ 
- Working with curl or some other HTTP client 
- Knowing JSON format 
- Basic git commands 


_links_ 

https://docs.roguewave.com/en/klocwork/current 

internal network: 

Web Api Reference - http://dvd12klw:8080/review/api 

Klocwork Server - http://dvd12klw:8080 

** See Help page in Klocwork server - very useful 

 

## Keywords
- static code analysis 
- Projects, Builds Modules and Views 
- Build Specification 
- checkers 
- Issues: states, status, severity 
- ltoken 
- klocwork rest api 

 

### binaries tools: 
- kwauth 
- kwadmin 
- kwsync 
- kwgradle(w) 
- kwinject 
- kwant 
- kwwarp 
- kwcheck 
- kwbuildproject 
- kwmaven 
- kwjava 
- kwciagent 

## Questions
1. What are the supported languages ? 
2. What is "build specification"? What are the klocwork tools (more than one) used to create it? 
3. Describe the three stages of basic Klocwork Scan. 
4. What is `ltoken` file? How to create it? Where is it located? What is its content?  
5. What are Modules and Views, give an example of their possible use? 
6. synchronizing between projects - explain a case which you use this tool  
7. Incremental builds? when to use them?  
8. What is distributed analysis for c/c++ ? 

## Exercises 

_Required infrastructure_
- A Virtual machine (Windows). 
- A service account (SVC_LAB_KW) 
- A Klocwork project
  - Ask a klocwork administrator  to open the project for you, name it “KW_LAB_<your_user_name>” (LINK to a list of KW admins)
  - Make sure he gives admin permissions for you and for SVC_LAB_KW 
- A demo C application (We have one in Git TBD: LINK to the relevant repo) 
- Binary tools for working with KW: 
    - Server Tools : \\dvd12klw01\KWServerTools\bin 
    - User Tools : \\dvd12klw01\KWUserTools\bin 


### Exercise 1 - Run KW scan for C/C++ 
1. log into the VM 
2. authenticate with the Klocwork Server to create klocwork token (use kwauth command - run as administrator) 
    - check if %USERPROFILE%\.klocwork\ltoken file was created 
3. clone test project from - <some test project from git> 
4. create build specification   
Project build command is: TBD
``` 
> MSBUILD …
```

5. run the integration build analysis 
6. upload the analysis result to the server 
7. enter the web server. see the build results. 
8. fix issue in file ….. 
9. run steps 4-6 and see the results on the server. 

### Exercise 2 - Web Requests - analyzing results 
For this task you can use powershell, python or any other script language. 

1. use some HTTP client to get data from the server - Web API Reference link above  
2. use search action to get the last build info   
Hints:
    - post request 
    - request body: `“action=search&user=<kw_username>&project=<kw_project>&ltoken=<user_token>” ` 
3. Write a script that will print:
    -  How many issues exist?  
    - How many issues are now?
    - What is the status of the issues? 
    - How many issues with severity “Review”? “Warning”? “Error”? “Critical”?  

 

*Advance* : use the report action to get the same results. 

### Exercise 3 - Create modules and view 

 

create module for the path pattern <TBD> 

exclude this module form the default view 

How many open issues exist now?  