# Send mail with fixed addressee via GMail

## Code
    {#settemp -name mailtitle -content {#replace {#formeditbox -text Title -single -required } -oldtext " -newtext \"}}{#settemp -name content -content {#replace {#formeditbox -text Content} -oldtext " -newtext \"}}{#run -file "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe"}{#sleep 300}{#focus Windows PowerShell -windowstate show}{#sleep 500}$EmailFrom = 'YOUR_GMAIL_ADDRESS@gmail.com';$EmailTo = 'ADDRESSEE-EMAIL-ADDRESS@example.com';$Subject = '{#gettemp mailtitle}';$Body = '{#gettemp content}';$SMTPServer = 'smtp.gmail.com';$SMTPClient = New-Object Net.Mail.SmtpClient($SmtpServer, 587);$SMTPClient.EnableSsl = $true;$SMTPClient.Credentials = New-Object System.Net.NetworkCredential('YOUR_GMAIL_ADDRESS@gmail.com', 'YOUR_GMAIL_PASSWORD');$SMTPClient.Send($EmailFrom, $EmailTo, $Subject, $Body);exit
    
    

To use this phrase, you need to change some values in above source code
 * `$EmailFrom = 'YOUR_GMAIL_ADDRESS@gmail.com'`: replace with your GMail address
 * `$EmailTo = 'ADDRESSEE-EMAIL-ADDRESS@example.com'`: replace with addressee's email address
 * `...NetworkCredential('YOUR_GMAIL_ADDRESS@gmail.com', 'YOUR_GMAIL_PASSWORD')...`: replace with your GMail login credentials
* One can also use other SMTP mail server by changing `$SMTPServer = 'smtp.gmail.com'`.


## Description
 * [Send email in Windows Powershell](http://www.howtogeek.com/120011/stupid-geek-tricks-how-to-send-email-from-the-command-line-in-windows-without-extra-software/)
 * Compatible with Windows 


## Usages
 * Add a new task into your [Omnifocus](https://www.omnigroup.com/omnifocus/), [Asana](https://app.asana.com/), etc. via Email
 
