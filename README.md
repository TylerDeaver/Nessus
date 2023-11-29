# Vulnerability Management with Tenable Nessus
![Nessus Title](https://github.com/TylerDeaver/Nessus/assets/149614301/fd8d437f-1566-44c2-9435-7c90f9c3413d)

## Summary and Purpose

This project is similar to the [Vulnerability Management with OpenVAS](https://github.com/TylerDeaver/OpenVAS) and [Vulnerability Management with Qualys](https://github.com/TylerDeaver/Qualys) projects.

In this project, Oracle VirtualBox was used to create a Linux virtual machine (VM), which hosted an outdated version of Ubuntu (18.04.6). In the previous vulnerability management projects, outdated software was used to ensure the machines were vulnerable. In this project, an outdated operating system (OS) was used to show the importance of keeping all aspects of a system, including the OS, up to date.

To highlight the significance of properly configuring vulnerability scans, two types of scans were conducted. First, an unauthenticated scan was performed on the VM. Following the completion of the unauthenticated scan, a credentialed scan was configured and initiated. Based on the results of the credentialed scan, remediations were implemented to mitigate major vulnerabilities. 

A final credentialed scan was conducted to verify the effectiveness of the implemented remediations.


## Technologies, Azure Components, and Regulations Used

- Oracle VirtualBox
- Tenable Nessus Vulnerability Scanner
- Linux (Ubuntu) Virtual Machine 

## Configure Virtual Machine and Nessus for an Unauthenticated Scan

To prepare the Linux VM, SSH was installed and the firewall was disabled  in order to allow Nessus access to the machine.

<br>Nessus was then configured to conduct an unauthenticated scan of the VM.

##  Results of the Unauthenticated Scan

Due to the scan being unauthenticated, the vulnerabilities found do not accurately reflect the vulnerabilities known to be on the machine. The outdated OS on the virtual machine is not reflected in this scan due to the limited capabilities inherent in unauthenticated scans.

![1 NonCred Scan Over](https://github.com/TylerDeaver/Nessus/assets/149614301/82438874-2bad-4361-a3c6-d30045dd2af3)
![2 NonCred Scan Vuln](https://github.com/TylerDeaver/Nessus/assets/149614301/f44bc8a9-ce97-4d5f-b43b-5b75415d6750)


## Configure Nessus for a Credentialed Scan

To configure the Nessus for a credentialed scan, the VM’s credentials were provided to the scanner.

![3 CredScan Config](https://github.com/TylerDeaver/Nessus/assets/149614301/94a79ea2-5762-4a01-afeb-f0f0b4e67c3f)


## Results of the Credentialed Scan

The difference in vulnerabilities discovered during the unauthenticated and credentialed scans is immediately apparent. During the unauthenticated scan, Nessus was only able to find 19 informational “vulnerabilities.” These are not true vulnerabilities, rather they are statements of fact about the scanned system.During the credentialed scan, Nessus found 53 critical vulnerabilities, 175 high vulnerabilities, and 73 medium vulnerabilities.

The credentialed scan allowed Nessus to fully evaluate the system, which included identifying vulnerabilities in the outdated OS. To learn more about the vulnerabilities, Nessus allows users to expand the details of any given vulnerability. 

![4 Cred Scan Over](https://github.com/TylerDeaver/Nessus/assets/149614301/6e32a428-5cbe-44a6-b859-eabbce863f11)
![5 Cred Scan Vuln](https://github.com/TylerDeaver/Nessus/assets/149614301/ab799a5a-aa3b-44d3-8702-70f4afb69e01)
![6 Cred Vuln Detail](https://github.com/TylerDeaver/Nessus/assets/149614301/4b1376ec-e23f-4986-9c28-035fbae15b9a)
![7 Cred Vuln Detail](https://github.com/TylerDeaver/Nessus/assets/149614301/2c68a792-bf7f-4a77-ba08-b511c3499f1c)


## Remediation, Verification Scan, and Conclusion

To remediate the majority of the vulnerabilities found during the credentialed scan, the OS was updated using SSH and PowerShell

![8 powershell update](https://github.com/TylerDeaver/Nessus/assets/149614301/eafe7c7d-c43b-487e-9bf9-2f84e3a12b26)


Another credentialed scan was performed to verify the remediation. While the remediation improved the security posture of the machine, there were still six critical vulnerabilities, 38 high vulnerabilities, and 23 medium vulnerabilities. 

![10 Cred Scan Over](https://github.com/TylerDeaver/Nessus/assets/149614301/5e65b802-5ce6-446c-aa77-4a670a59dc64)
![11 Remediations](https://github.com/TylerDeaver/Nessus/assets/149614301/21ffa3f9-8cd4-4ac1-897a-6471d5005676)


When viewing the suggested remediations, it is clear these vulnerabilities are primarily due to Ubuntu 18.04.6 no longer being supported. To remediate the vast majority of the remaining vulnerabilities, the VM was given access to the internet and was upgraded from Ubuntu 18.04.6 to Ubuntu 20.04. 

![12 Forced Upgrade](https://github.com/TylerDeaver/Nessus/assets/149614301/899de78a-63cf-47ba-99e2-1be62b74eeab)


A final credentialed scan was performed. This credentialed scan results returned with only one high vulnerability and one medium vulnerability. For the purpose of this project, these two vulnerabilities were deemed as acceptable and left in place.

![13 Cred scan UPGRADE](https://github.com/TylerDeaver/Nessus/assets/149614301/cd6c80dd-631c-4f2d-a131-41d70c8389c5)
![14 detail](https://github.com/TylerDeaver/Nessus/assets/149614301/3b96ddb0-da1b-49e6-a15c-89918d1034fe)
![15 Python vuln](https://github.com/TylerDeaver/Nessus/assets/149614301/547a3610-7605-43b7-9760-972cdfc5b4fb)


In total, the remediation done in this project decreased the known vulnerabilities from 301 to two.

This project successfully demonstrated the configuration of Nessus and the subsequent remediation of vulnerabilities. The project also demonstrated the importance of conducting credentialed scans when possible, as an unauthenticated scan does not accurately reflect the security of a system.

## Reflection
This project was designed to give me hands-on experience with vulnerability management, to include configurations and remediations. This project directly relates to my other vulnerability management projects and was a great way to become more comfortable with different vulnerability management tools.



