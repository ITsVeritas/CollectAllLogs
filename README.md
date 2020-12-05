# CollectAllLogs
CollectAllLogs is designed to be used with the Run Scripts feature of MECM (SCCM). It will collect many logs from a device or collection of devices, upload them to
a management point, and send a status message which causes the primary to copy the zip from the management point to a directory of choice.

1. Copy Microsoft.ConfigurationManagement.Messaging.dll to <ConfigMgr Installation Dir>\CCM\Incoming\MessagingDll and \SMS_CCM\Temp on each Management Point
2. Create a new “Run Script” using the contents of the script “CollectAllLogs.ps1”.
3. Place the MoveLogtoPrimary.ps1 to the primary site server in a <SCRIPTSDIR> of choice.
4. Create a directory for logs <COLLECTALLLOGSDIR>
5. Create a status filter rule with Message ID 1234
6. On the Actions Tab, check “Run a Program”
Command line:
"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -executionpolicy bypass -file "<SCRIPTSDIR>\MoveLogtoPrimary.ps1" -InsString1 %msgis01 -InsString2 %msgis02 -PrimaryLogFolder <COLLECTALLLOGSDIR>
7. Move status filter rule up in priority to the top
8. Right-click a device in the MECM console
9. Click Run Script
10. Select “Collect All Logs”
11. Check the path chosen at <CollectAllLogsDir> for a .zip file after a few minutes
