Just a few notes.

It needs JDK 1.6. The original documentation says that it works with Exchange 2010
but it seems to work against Exchange 2007 Service Pack 1.

Modified Appointment.java, method validate(): lines 239-258 commented out
This removes the requirement that a TimeZoneDefinition be added for Appointment's
save & update calls to Exchange 2007 SP1 (only). Exchange 2007 SP1 was choking
on the TimeZoneDefinition elements in the request. With these changes, save(...)
should work as documented.

Modified ExchangeServiceBase.java method convertDateTimeToUniversalDateTimeString():
line 566 added to force formatter to be using UTC by default. (Earlier setting of
formatter class default to PST in application seems to have caused problems)

Altered visibility of constructor AutodiscoverService(ExchangeServiceBase) to public.

From the website:

Hello EWS Java experts. We have posted an updated EWS Java API package. 
Please note that this package has new list of pre-requisities:
 - Apache Commons HttpClient 3.1
 - Apache Commons Codec 1.4
 - Apache Commons Logging 1.1.1
 - JCIFS 1.3.15.
We made these changes to address issues with incorrect credential caching for 
some types of multi-threaded client implementations caused by a bug 
(http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6626700) with java.net.HttpURLConnection 
(http://download.oracle.com/javase/6/docs/api/java/net/HttpURLConnection.html). 
Thanks for your patience and please let us know if you run into any problems.
