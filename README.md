# curl-problem
Solutions for curl problem sheet

1) Git repository created via distant repository, i.e., https://github.com and cloned to local machince using: git clone https://github.com/EddyCodeIt/curl-problem.git
Alternatively we can create local repository on machine via command promt(git bash), but requires more steps.

2) To download HTML file of this URL: https://www.jmarshall.com/easy/http/ , I used a cURL command: curl https://www.jmarshall.com/easy/http/ > http-easy.html

   Upon examining differance between URL and locally stored html page of this website, I noticed that browser does not make a request to a server when opening localy stored files. URL of local file looks something like this: file:///C:/Users/eduar/Desktop/Data_Rep_Q/curl-problem/http-easy.html
   
        Note: > symbol in stdout stream redirects stream to something what you specify, e.g., text file or some other types of files.

3) 
  3.1 Attempt to download duckduckgo.html using normal download method: curl https://www.duckduckgo.com > duckduckgo.html

        Result: Status 301 Moved Permanently
        
  Problems is that by default curl doesn't redirect to HTTP location of duckduckgo.com which is located in Header.
        Sulution: use -L after curl. -L option picks up HTTP Location and redirects to actual page location
  When compairing source code of downloaded file and source code of a page, I see no differance once again like in problem 2. Only differance is in URL.
  
  3.2 To obtain verbose mode details I use option -v. It displays transactions between client and server. In this case my machince is a client sending request to the server. 

  Full command: curl -v duckduckgo.com
  
  To output verbose mode details to a text file I tried a command: curl -v duckduckgo.com > verbus.txt. 

        Result: output of a text file showed me once again: Status 301 Moved Permanently
  
  After some research on web I found few solutions to output verbose details to a text file:
        1. curl -v duckduckgo.com --stderr duckduckgo.txt 
           option --stderr is used for outputing diagnostical and debug messages in a text format, and then it can be saved to a file
        2. Instead of --stderr you can use curl ...    2> filename. This will produce same result.
        3. curl ... > filename 2>&1. This will get both stdout and stderr into a same file
        
        Information source: https://curl.haxx.se/mail/archive-2005-06/0090.html
        
4) 
    4.1 When searching for GMIT using duckduckgo search engine it produces following URL: https://duckduckgo.com/?q=GMIT&t=h_&ia=about
    To adapt this URL to search for science I swapped GMIT for science in URL.
    In attempt to save a response, using curl and URL https://duckduckgo.com/?q=science&t=h_&ia=about, I received few errors: 
    
        't' is not recognized as an internal or external command, operable program or batch file.
        'ia' is not recognized as an internal or external command, operable program or batch file.
        
    By looking at URL again I noticed this parameters: &t=h_&ia=about
        Info source for &t= : https://duck.co/help/privacy/t
    
    The problem is that curl reads this parameters as external/internal commands and have to be removed before sending a request. 
    
        Note: to save output to a file you can use: 'curl -o filename.txt URL' OR 'curl URL > filename.txt' to also output data to console
        
    4.2 To make a request to duckduckgo to search for 'computer science', modify URL as follows: 
            https://duckduckgo.com/?q=science to https://duckduckgo.com/?q=computer+science
            Note: how words are separated by + sign
            
    
