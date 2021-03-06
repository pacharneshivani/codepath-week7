# Week 7 Project: WordPress vs. Kali

Time spent: **9** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Report

1. Vulnerability Name or ID: Authenticated Stored Cross-Site Scripting
  - [x] Summary: Cross-site scripting vulnerability in the text editor box in pages and writing/editing posts.
    - Vulnerability types: XSS
    - Tested in version: 4.2.2 
    - Fixed in version: 4.2.3
  - [x] GIF Walkthrough: <img src='https://i.imgur.com/9jwGn1R.gif' title='Video Walkthrough' alt='Video Walkthrough' />
  - [x] [Better quality GIF](https://i.imgur.com/VHB6dsI.gif)
  - [x] Steps to recreate: In post/page editor mode, when logged in from contributor (whose post, if approved blindingly) and above, can type in "<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>" triggering XSS in text editor mode. 
  - [x] Affected source code: 
    - [Reference](https://klikki.fi/adv/wordpress3.html)
    - [Changelog](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/class-wp-editor.php?rev=33361)
2. Vulnerability Name or ID: User enumeration using wpscan
  - [x] Summary: Because the error messages displayed are different when a non-existent username is entered vs when an invalid password is entered for an existing user, wpscan is able to enumerate the users, even those that have never posted, commented nor contributed.
    - Vulnerability types: User enumeration
    - Tested in version: 4.2.2
    - Fixed in version: -
  - [x] GIF Walkthrough: <img src='https://i.imgur.com/j5Kkfwu.gif' title='Video Walkthrough' alt='Video Walkthrough' />
  - [x] [Better quality GIF](https://i.imgur.com/gHyTwKu.gif)
  - [x] Steps to recreate: Run "wpscan --url [INSERT_WORDPRESS_URL_NAME] --enumerate u" in kali linux.
  - [x] Affected source code:
    - [Reference](https://www.wpwhitesecurity.com/wordpress-security/wordpress-username-disclosure-vulnerability/)
    - [GitHub](https://github.com/WordPress/WordPress/blob/4.2-branch/wp-login.php)
3. Vulnerability Name or ID: Password Brute Force Attack
  - [x] Summary: Using rockyou.txt wordlist and wpscan, together with the user enumeration shown in number 2, the password of a particular username can be guessed by brute force because wordpress by default does not limit the number of login attempts.
    - Vulnerability types: Login Vulnerability
    - Tested in version: 4.2.2
    - Fixed in version: -
  - [x] GIF Walkthrough: <img src='https://i.imgur.com/anikNCL.gif' title='Video Walkthrough' alt='Video Walkthrough' />
  - [x] [Better quality GIF](https://i.imgur.com/JuRY8cF.gif)
  - [x] Steps to recreate: Download the rockyou.txt dictionary file through `apt-get install wordlists`. Run "wpscan --url [INSERT_WORDPRESS_URL_NAME] --enumerate u" in kali linux (to enumerate users). Then, run "wpscan --url [INSERT_WORDPRESS_URL_NAME] --wordlist [PATH_TO_ROCKYOU_DICTIONARY - usually, it's /usr/share/wordlists/rockyou.txt" --username [USERNAME_YOU_FOUND_FROM_USER_ENUMERATION]" in kali linux.
  - [x] Affected source code:
    - [GitHub](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

N/A

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

N/A

## License

    Copyright [2017] [Shivani Pacharne]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
