## .NET RegEx Examples

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
