# Wordpress-
Codepath week 7-8
## CVE-2015-3440: Stored XSS in a comment
### Surces:https://klikki.fi/adv/wordpress2.html, https://www.exploit-db.com/exploits/36844

### Overview:
  Many of the wordpress version before 4.2.1 were vulnerable to stored cross-site -scripting attacks. Attcackers can inject Javascript in a comment in a post and the attack would commence once the administrator has approved of a previous comment.
  Once the code has been triggered, the attacker can act as the administrator and change the password, add a new post, etc.
  
### Details
  
    First, the attacker would need to post a harmless comment so that the adminstrator could approve the comment.
    After the administrator approves a single comment from a user(the attacker in this case), the user will no longer need approval for any of the further comments.
    After the first comment is approved, the attacker can then post a comment(which is the script in this case).
    The script would need to be 64kb long.
    
 ## Proof of Concept
 ![](Wordpress/images/Screenshot(70).png)
    Comment for attack:
    "<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>"
