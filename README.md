How-to-create-a-vb.net-application-to-send-sms
==============================================

With this code you can create an application to send ip sms.

With a VB.Net programming language you are able to write or implement an sms sending / receiving solution to your system in a fast and easy way.

**Prerequisites to send / receive sms messages in Vb.Net**

This code is written in VB.Net, so you need an IDE (Integrated Development Environment) supporting this programming language, such as Microsoft Visual Studio.

This method  is based by sending a http request to an SMS Gateway so you will need one. I already use an SMS Gateway so I show the example with this software.

I have a direct SMPP connection so there can be difference in sending sms with a gsm modem.

**Creating the IDE to start writing the application**

* Open the Visual Studio software
* Create a new project by clickin the file->new project-> new windows form application
* Open the code sheet and start writing the code

**Writing the code**

*Step -  1. Connection to SMS Gateway.*

If you open the create a new project, and start the following section in the code section:
```
Dim request As HttpWebRequest
Dim response As HttpWebResponse = Nothing
Dim url As String
Dim username As String = "admin"
Dim password As String = "abc123"
Dim host As String = "http://127.0.0.1:9501"
Dim originator As String = "06201234567"
```

With these commands you can connect to the SMS Gateway. This code specifies that you will send a http request, it will provide you username, password, host- and phone number to the SMS Gateway. Modify these values to match with your personal data.

*Step -  2 – Composition of the URL*

 This is the code for creating an URL. This code will be posted to the SMS Gateway.
```
url = host + "/api?action=sendmessage&" _
& "username=" & HttpUtility.UrlEncode(username) _
& "&password=" + HttpUtility.UrlEncode(password) _
& "&recipient=" + HttpUtility.UrlEncode(tbReceiver.Text) _
& "&messagetype=SMS:TEXT" _
& "&messagedata=" + HttpUtility.UrlEncode(tbMessage.Text) _
& "&originator=" + HttpUtility.UrlEncode(originator) _
& "&serviceprovider=" _
& "&responseformat=html"
```

Sender’s username: Captures your login name. 
Sender’s password: Captures your password. 
Recipient: Captures the recipients number. 
Message type: Type of message. In this case text sms 
Message data: Captures the content of message. The SMS will be a text message 
Originator: Captures the sender’s phone number.
Service provider: Captures the name wich service provider you wish to send the text message
Response format: Captures the answer’s type.  

*Step -  3 - Submit the URL*

To send your SMS message you need to initiate a HTTP request.   This is the code to add how you wish to send the URL out.

```request = DirectCast(WebRequest.Create(url), HttpWebRequest)```

This row presents the method of the answer.

```response = DirectCast(request.GetResponse(), HttpWebResponse)```

The following code provides the method, how the answer should be displayed.

```MessageBox.Show("Response: " & response.StatusDescription)```

After you gave what the URL have to contain what will be it’s route and how the application should answer you click ont he run application button and your message will sent.
Please note that as you test your application, take care of any expenses you may be generating for yourself or another person as you sending the text messages.

**References:**

http://code.msdn.microsoft.com/wpapps/Sending-SMS-Using-PC-COM-3d79e1d7

http://www.codeproject.com/Articles/15299/Send-a-Text-Message-to-a-Cell-Phone-from-a-VB-NET

http://ozekisms.com/index.php?owpn=587&info=send-receive-sms-from-vb-sms-http

http://www.digitalbuzzblog.com/2011-mobile-statistics-stats-facts-marketing-infographic/

**Download link to softwares:**

Download Microsoft Visual Studio: http://www.microsoft.com/hu-hu/download/visualstudio.aspx?q=visual+studio

Download Ozeki NG SMS Gateway: http://ozekisms.com/index.php?owpn=112
