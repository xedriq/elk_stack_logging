logs message should have:
request id: can be that twitter handle
request with response data duration
request initiated datetime
request done datetime
response status

### To set client machine to push logs to remote server

Above the line “#First some standard log files. Log by facility” we’ll add the following:

*.*                         @@127.0.0.1:10514