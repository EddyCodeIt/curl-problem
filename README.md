# curl-problem
Solutions for curl problem sheet

1) Git repository created via distant repository, i.e., https://github.com and cloned to local machince using: git clone https://github.com/EddyCodeIt/curl-problem.git
Alternatively we can create local repository on machine via command promt(git bash), but requires more steps.

2) To download HTML file of this URL: https://www.jmarshall.com/easy/http/ , I used a cURL command: curl https://www.jmarshall.com/easy/http/ > http-easy.html

   Upon examining differance between URL and locally stored html page of this website, I noticed that browser does not make a request to a server when opening localy stored files. URL of local file looks something like this: file:///C:/Users/eduar/Desktop/Data_Rep_Q/curl-problem/http-easy.html
