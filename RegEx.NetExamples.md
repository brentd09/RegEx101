## .NET RegEx Examples

```PowerShell
# List only network sockets that are in a LISTENING state

netstat -ano | Select-String -Pattern 'LISTENING'
```

---

```PowerShell
# Matching a Class C IP address

'221.1.1.255'  -match '^(19[2-9]|2[0-1][0-9]|22[0-3])(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])){3}$'
'229.10.21.62' -match '^(19[2-9]|2[0-1][0-9]|22[0-3])(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])){3}$'
'191.0.0.12'   -match '^(19[2-9]|2[0-1][0-9]|22[0-3])(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])){3}$'
'10.41.41.42'  -match '^(19[2-9]|2[0-1][0-9]|22[0-3])(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])){3}$'
```

---

```PowerShell
# Split a string into an array based on a regex pattern

$OctetArray = '131.107.0.3' -split '\.'
$OctetArray[1]
```

---

```PowerShell
# Replace the older em html tag with the newer strong ones

$Html = '<p>Hello there <em>EVERYONE</em> this previous word was emphasised</p>' 

$Html -replace 'em', 'strong' # this line fails as it also alters emphasised
$Html -replace 'em(?=>)', 'strong' # This line succeeds because it needs to match
                                   # the assertions before the replace action happens
                                   # If the assertion fails the match will not be replaced
```

---

```PowerShell
# Using RegEx to validate input to the script, this can be used to write a different
# SQL query based on the type of information supplied to the script

$WhoAreYou = Read-Host -Prompt 'Enter an Email Address or Phone Number to help us identify you'

switch -regex ($WhoAreYou)
{
    '.*@\w{2,}(\.\w{2,})*' {Write-Host -ForegroundColor Cyan "$WhoAreYou - is a valid email address"}
    '\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d[ -]*\d' {Write-Host -ForegroundColor Green "$WhoAreYou - is a valid phone number"}
    Default {Write-Host -ForegroundColor Red "$WhoAreYou - Cannot be used to identify you"}
}
```

---

```PowerShell
# Receiving raw data from analog to digital weather devices 
# Extracting the data via RegEx in Powershell

$WeatherData = @'
20231010090010242384
20231010090110232186
20231010090210242586
20231010090310252680
20231010090410262779
20231010090510252875
'@

$Pattern = '(\d{4})(\d{2})(\d{2})(\d{2})(\d{2})(\d{4})(\d{2})(\d{2})'
$WeatherRegEx = [regex]::new($Pattern,'Multiline,Compiled')

$WeatherCsv = $WeatherRegEx.Replace($WeatherData,'$1,$2,$3,$4,$5,$6,$7,$8')
$WeatherCsv | ConvertFrom-Csv -Header 'Year','Month','Day','Hour','Minute','Pressure','Temperature','Humidity'
```

---

```PowerShell
# Credit Card masking
# Handle spaces or dashes or nothing between the numbers

$CardNumbers = @'
1234-1234-1234-1234
3011-3012-3013-3014
2933923393229211
3131323212132321
4321 4321 4321 4321
'@

$Pattern = '^\d{4}[ -]?\d{4}[ -]?\d{4}[ -]?(\d{4})?'
$CardRegEx = [regex]::New($Pattern,'Multiline,Compiled')

$CardRegEx.Replace($CardNumbers,'XXXX-XXXX-XXXX-$1')
```

---

```PowerShell
# Converting the correct spaces into commas
# With the person's name having a different amount of words this can be difficult
# Then converting the CSV into PowerShell Objects

$List = @'
Name Department City
John Deering Sales Sydney
Ken Brooks IT Brisbane
Lina Bridges Accounts Melbourne
Don A Wetts Sales Sydney
'@

$RegEx = [regex]::New(' (?=[A-Za-z]+ ?[A-Za-z]*$)','multiline')
$RegEx.Replace($List,',') | ConvertFrom-Csv
```

---

```PowerShell
# Converting a space just before a word boundary to a comma
# then converting the CSV format into PowerShell Objects 

$List = @'
UserID   Department    City         
JohnD    Sales         Sydney       
KenB     IT            Brisbane    
LinaB    Accounts      Melbourne 
DonW     Sales         Sydney
'@

$RegEx = [regex]::new(' (?=\b)','multiline')
$RegEx.Replace($List,',') | ConvertFrom-Csv
```

---

```PowerShell

```
