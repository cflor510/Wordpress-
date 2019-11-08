# Wordpress-
Codepath week 7-8
## CVE-2015-3440: Stored XSS in a comment
### Sources:https://klikki.fi/adv/wordpress2.html, https://www.exploit-db.com/exploits/36844

### Overview:
  Many of the wordpress version before 4.2.1 were vulnerable to stored cross-site -scripting attacks. Attcackers can inject Javascript in a comment in a post and the attack would commence once the administrator has approved of a previous comment.
  Once the code has been triggered, the attacker can act as the administrator and change the password, add a new post, etc.
  
### Walkthrough:
  
    First, the attacker would need to post a harmless comment so that the adminstrator could approve the comment.
    After the administrator approves a single comment from a user(the attacker in this case), the user will no longer need approval for any of the further comments. 
    I had problems with this step because i wasn able to view posts at first. I kept getting a 404 error
 ![404 request when attempting to view page](images/Screenshot77.png)
    I had to change the permalink settings from "Custom Structure" to "Default"
 ![Change to default Permalink settings](images/Screenshot78.png)
    After the first comment is approved, the attacker can then post a comment(which is the script in this case).
    The script would need to be 64kb long.
 ![Script used for attack](images/Screenshot70.png)
 
    
 ## Attack Confirmation
    After the comment with the script is posted, you can see the the alert box that shows you the script worked
 ![Attack succes](images/Screenshot69.png)



## CVE-2016-7168 Authenticated Stored Cross-Site Scripting via Image Filename
### Sources:https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html

### Overview:

    Using this persistant cross site scrpting attack, an attacker can manipulate an admin(via social engineering) to upload an image with a malicious filenam. When uploaded into wordpress, will allow the attacker to steal the admins session cookies and login info to act as the admin and manipulate the site.
    
### Walkthrough:
