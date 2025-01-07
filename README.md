# MassCyberCenter-Mentorship-Project-

<h2> Overview </h2>
<p>This repository documents my journey and deliverables during the MassCyber Center mentorship program. This mentorship program tasked us with completing a cybersecurity project and then presenting it at a showcase event attended by cybersecurity professionals. The goal for this project was to build, break, secure, and administer a virtual machine. Specifically, my goal was to exploit a known Gitlab vulernability, CVE-2023-2825, to understand security weaknesses and implement mitigation strategies.</p>

<h2> <strong></strong>Building the Machine</strong></h2>
<p> To build the virtual machine, I utilized VirtualBox, a powerful x86 and AMD64/Intel64 virtualization product. </p>
<p> Environment Setup: </p>
<ul>
  <li>Installed VirtualBox </li>
 <li> OS: Ubuntu 24.0.4.1</li> </li>
<li>CPU: 2 Processors </li>
<li>Memory: 4096 MB</li>
<li>Disk Space: 64 GB </li>
<li> Additional Software: GitLab 16.0.0 </li>
</ul>

<img width="400" alt="vm_config" src="https://github.com/user-attachments/assets/ce95148e-a2aa-4e37-b5ab-ce37e593a800" />

<h2> Breaking the Machine</h2>
<p>GitLab version 16.0.0 was installed on the VM, which is affected by <strong>CVE-2023-2828</strong>, a vulnerability that allows unauthenticated users to read arbitrary files on the server by exploiting a path traversal bug. After conducting extensive research, I found a publicly available exploit on GitHub here: <a href="https://github.com/Occamsec/CVE-2023-2825" target="_blank">Occamsec for CVE-2023-2825</a>. </p>
<p>For this project, I customized the exploit by editing the original Python code to allow user input at runtime and implementing error handling to make the script more interactive and robust. Below are the steps I followed to implement and execute the exploit on the vulnerable VM:</p>

<ol>
  <li><strong>Allow User Input:</strong> I edited the code to allow for runtime input, so the user could easily enter the endpoint and credentials. </li>
  <li><strong>Implement Error Handling:</strong> I added error handling to manage potential issues, such as incorrect file paths or network failures. The code now provides useful feedback to the user in case of errors. </li>


<img width="649" alt="exploit" src="https://github.com/user-attachments/assets/15f5357e-d7e2-4370-8340-bdc1317fc931" />

<li><strong> Running the Exploit: </strong> I saved my python code under 'attack3.py', in which I then executed by running 'python3 attack3.py in the Ubuntu terminal. After running the script, I was able to access the specified file , which was'/etc/passwd'.  </li>
</ol>


<img width="650" alt="exploit_result" src="https://github.com/user-attachments/assets/e6ea4de6-f6e2-4b26-ae74-eddc47b8a4eb" />

<h2> <strong>Securing the Virtual Machine </strong></h2>
<p> In order to secure the VM, I updated to the latest Gitlab patch version, which was 17.5.1. Here are some steps I took in order to do so:  </p>
<ol>
  <li> <strong>Verify current version: </strong>   </li>
   <code> gitlab-rake gitlab:env:info </code>
   <li><strong>Backup Gitlab data: </strong> </li>
   <code>sudo gitlab-backup create</code>
   <li><strong>Install latest Gitlab version: </strong> </li>
    <code>sudo apt-get update</code>
    <code>sudo apt-get install gitlab-ee</code>
   <li><strong>Restart Gitlab: </strong></li>
   <code>sudo gitlab-ctl restart</code>
   <li><strong>Verify the update:</strong></li>
   <code>gitlab-rake gitlab:env:info</code>
</ol>
<h2>Administering the Machine:</h2>
<p>To administer the VM effectively, I implemented several measures to ensure secure and efficient management. These included restricting administrative access, applying regular updates, and following best practices for system administration: </p
<ol>
  <li><strong> Restricting Administrative Access:</strong> Check what users have administrative access. </li>
  <code>getent group sudo </code>
  <li><strong> Check for latest updates and patches by frequently visiting:</strong> <a href="https://about.gitlab.com/releases/categories/releases/" target="_blank">
    GitLab Releases Page</a></li>
</ol>

<h2>Conclusion and Reflections</h2>
<p>This project was an incredible learning experience that allowed me to delve deep into the lifecycle of a virtual machine—from building and exploiting vulnerabilities to securing and administering it. By exploiting CVE-2022-2825, I gained valuable insights into identifying and mitigating real-world security threats. The process of securing the VM reinforced the importance of proactive system maintenance and staying updated with the latest patches and best practices.</p>
<p>Through this mentorship program, I honed my skills in:</p>
<ul>
  <li>Setting up and configuring virtual machines.</li>
  <li>Researching and implementing security patches for known vulnerabilities.</li>
  <li>Adapting existing exploits and integrating user input for testing purposes.</li>
  <li>Administering and hardening systems against potential threats.</li>
</ul>
<p>Overall, this experience has strengthened my technical abilities and deepened my understanding of cybersecurity. It has also underscored the critical role of vigilance and continuous learning in protecting systems against evolving threats.</p>
<p>I am grateful for the guidance provided by the MassCyberCenter mentorship program and look forward to applying these skills to future challenges in cybersecurity</p>

