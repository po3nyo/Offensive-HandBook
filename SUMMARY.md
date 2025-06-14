# Table of contents

* [Introduction](README.md)

## 📌 Pinned

* [Cheat Sheet](pinned/cheat-sheet/README.md)
  * [MSFVenom-Cheatsheet](pinned/cheat-sheet/msfvenom-cheatsheet.md)
  * [Hydra-Cheatsheet](pinned/cheat-sheet/hydra-cheatsheet.md)
  * [Hashcat-Cheatsheet](pinned/cheat-sheet/hashcat-cheatsheet.md)

## 📖 background knowledge

* [Active Directory & Windows](background-knowledge/active-directory-and-windows/README.md)
  * [PowerShell](background-knowledge/active-directory-and-windows/powershell/README.md)
    * [SC (Service Control)](background-knowledge/active-directory-and-windows/powershell/sc-service-control.md)
  * [AD-Port](background-knowledge/active-directory-and-windows/ad-port.md)

***

* [Linux](linux/README.md)
* [Web](web.md)
* [Network](network.md)
* [CS](cs.md)

## 🟥 Offensive Security

* [Red Team Infrastructure](offensive-security/red-team-infrastructure.md)
* [Blue Team Infrastructure](offensive-security/blue-team-infrastructure.md)
* [Reconnaissance](offensive-security/reconnaissance.md)
* [Initial Access](offensive-security/initial-access.md)

***

* [Execution](execution.md)
* [Persistence](persistence.md)
* [Privilege Escalation](privilege-escalation.md)
  * [Linux](privilege-escalation/linux/README.md)
    * [Kernel Exploits](privilege-escalation/linux/kernel-exploits.md)
    * [Sudo](privilege-escalation/linux/sudo.md)
    * [SUID / SGID](privilege-escalation/linux/suid-sgid.md)
    * [Capability](privilege-escalation/linux/capability.md)
    * [Cron Jobs](privilege-escalation/linux/cron-jobs.md)
    * [PATH](privilege-escalation/linux/path.md)
    * [NFS](privilege-escalation/linux/nfs.md)
  * [Active Directory](privilege-escalation/active-directory.md)
  * [Windows](privilege-escalation/windows.md)
* [Defense Evasion](defense-evasion.md)
* [Credential Access](credential-access.md)
* [Discovery](discovery.md)
* [Lateral Movement](lateral-movement.md)
* [Collection](collection.md)
* [Exfiltration](exfiltration.md)
* [Command and Control](command-and-control.md)

## 🟦 Web Pentesting

* [Server-Side](web-pentesting/server-side/README.md)
  * [SQL injection](web-pentesting/server-side/sql-injection.md)
  * [Authentication](web-pentesting/server-side/authentication.md)
  * [Directory traversal](web-pentesting/server-side/directory-traversal.md)
  * [Command injection](web-pentesting/server-side/command-injection.md)
  * [Business logic vulnerabilities](web-pentesting/server-side/business-logic-vulnerabilities.md)
  * [Information disclosure](web-pentesting/server-side/information-disclosure.md)
  * [Access control](web-pentesting/server-side/access-control.md)
  * [File upload vulnerabilities](web-pentesting/server-side/file-upload-vulnerabilities.md)
  * [Race conditions](web-pentesting/server-side/race-conditions.md)
  * [Server-side request forgery (SSRF)](web-pentesting/server-side/server-side-request-forgery-ssrf.md)
  * [XXE injection](web-pentesting/server-side/xxe-injection.md)
  * [NoSQL injection](web-pentesting/server-side/nosql-injection.md)
  * [API testing](web-pentesting/server-side/api-testing.md)
  * [Web cache deception](web-pentesting/server-side/web-cache-deception.md)
  * [Insecure deserialization](web-pentesting/server-side/insecure-deserialization.md)
  * [GraphQL API vulnerabilities](web-pentesting/server-side/graphql-api-vulnerabilities.md)
  * [Server-side template injection (SSTI)](web-pentesting/server-side/server-side-template-injection-ssti.md)
  * [Web cache poisoning](web-pentesting/server-side/web-cache-poisoning.md)
  * [HTTP Host header attacks](web-pentesting/server-side/http-host-header-attacks.md)
  * [HTTP request smuggling](web-pentesting/server-side/http-request-smuggling.md)
  * [OAuth authentication](web-pentesting/server-side/oauth-authentication.md)
  * [JWT attacks](web-pentesting/server-side/jwt-attacks.md)

***

* [Client-Side](client-side/README.md)
  * [Cross-site scripting (XSS)](client-side/cross-site-scripting-xss.md)
  * [Cross-site request forgery (CSRF)](client-side/cross-site-request-forgery-csrf.md)
  * [Cross-origin resource sharing (CORS)](client-side/cross-origin-resource-sharing-cors.md)
  * [Clickjacking](client-side/clickjacking.md)
  * [Dom-based vulnerabilities](client-side/dom-based-vulnerabilities.md)
  * [WebSockets](client-side/websockets.md)
  * [Web LLM attacks](client-side/web-llm-attacks.md)
  * [Prototype pollution](client-side/prototype-pollution.md)

## 🟩 Mobile Pentesting

* [Android](mobile-pentesting/android.md)

***

* [IOS](ios.md)

## 🟨 reverse engineering

* [Reverse Engineering](reverse-engineering/reverse-engineering.md)

## 🟧 forensic

* [Windows](forensic/windows.md)
* [Linux](forensic/linux.md)

## 🟫 ETC

* [Tools](etc/tools/README.md)
  * [Reconnaissance / OSINT](etc/tools/reconnaissance-osint/README.md)
    * [Nmap](etc/tools/reconnaissance-osint/nmap.md)
    * [Rustscan](etc/tools/reconnaissance-osint/rustscan.md)
    * [Amass](etc/tools/reconnaissance-osint/amass.md)
    * [Subfinder](etc/tools/reconnaissance-osint/subfinder.md)
    * [Katana](etc/tools/reconnaissance-osint/katana.md)
    * [Nuclei](etc/tools/reconnaissance-osint/nuclei.md)
  * [Web Application Testing](etc/tools/web-application-testing/README.md)
    * [BurpSuite](etc/tools/web-application-testing/burpsuite.md)
    * [Caido](etc/tools/web-application-testing/caido.md)
    * [Feroxbuster](etc/tools/web-application-testing/feroxbuster.md)
    * [gobuster](etc/tools/web-application-testing/gobuster.md)
    * [Nikto](etc/tools/web-application-testing/nikto.md)
    * [Wpscan](etc/tools/web-application-testing/wpscan.md)
    * [ffuf](etc/tools/web-application-testing/ffuf.md)
    * [wfuzz](etc/tools/web-application-testing/wfuzz.md)
    * [Sqlmap](etc/tools/web-application-testing/sqlmap.md)
    * [Ghauri](etc/tools/web-application-testing/ghauri.md)
  * [Vulnerability Scanning / Exploitation](etc/tools/vulnerability-scanning-exploitation/README.md)
    * [Nessus](etc/tools/vulnerability-scanning-exploitation/nessus.md)
    * [Invicti](etc/tools/vulnerability-scanning-exploitation/invicti.md)
    * [HCL Appscan](etc/tools/vulnerability-scanning-exploitation/hcl-appscan.md)
    * [OpenVas](etc/tools/vulnerability-scanning-exploitation/openvas.md)
    * [Metasploit Framework](etc/tools/vulnerability-scanning-exploitation/metasploit-framework.md)
  * [Credential Dumping / Password Cracking](etc/tools/credential-dumping-password-cracking/README.md)
    * [Hydra](etc/tools/credential-dumping-password-cracking/hydra.md)
    * [Hashcat](etc/tools/credential-dumping-password-cracking/hashcat.md)
    * [John The Ripper](etc/tools/credential-dumping-password-cracking/john-the-ripper.md)
    * [Page](etc/tools/credential-dumping-password-cracking/page.md)
  * [Privilege Escalation](etc/tools/privilege-escalation.md)
  * [Active Directory / 내부망 공격](etc/tools/active-directory/README.md)
    * [Blood-hound](etc/tools/active-directory/blood-hound.md)
    * [Impacket](etc/tools/active-directory/impacket.md)
    * [Rubeus](etc/tools/active-directory/rubeus.md)
    * [CrackMapExec / Netexec](etc/tools/active-directory/crackmapexec-netexec.md)
    * [Powerview](etc/tools/active-directory/powerview.md)
    * [Kerberute](etc/tools/active-directory/kerberute.md)
    * [Certify](etc/tools/active-directory/certify.md)
    * [Responder](etc/tools/active-directory/responder.md)
  * [Tunneling / Proxy / C2](etc/tools/tunneling-proxy-c2/README.md)
    * [Ngrok](etc/tools/tunneling-proxy-c2/ngrok.md)
    * [Serveo](etc/tools/tunneling-proxy-c2/serveo.md)
    * [Chisel](etc/tools/tunneling-proxy-c2/chisel.md)
    * [Ligolo-ng](etc/tools/tunneling-proxy-c2/ligolo-ng.md)
    * [CoboltStrike](etc/tools/tunneling-proxy-c2/coboltstrike.md)
    * [Havoc](etc/tools/tunneling-proxy-c2/havoc.md)
    * [Mythic](etc/tools/tunneling-proxy-c2/mythic.md)
    * [Sliver](etc/tools/tunneling-proxy-c2/sliver.md)
    * [AdaptixC2](etc/tools/tunneling-proxy-c2/adaptixc2.md)
  * [Wireless / Nework Attack](etc/tools/wireless-nework-attack.md)
  * [Mobile](etc/tools/mobile.md)
  * [Reverse Enginnering](etc/tools/reverse-enginnering.md)
  * [Forensic](etc/tools/forensic.md)
* [CVE Research](etc/cve-research.md)
