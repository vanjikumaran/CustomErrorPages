CustomErrorPages
================

Custom Error pages for WSO2 carbon servers



WSO2 carbon servers are use to display the errors/Exceptions/Http status code in full detail manner or known as Verbose error messages. So the error messages contains technical details such as stack traces. As error messages tend to be unpredictable, other sensitive details may end up being disclosed. As impact on system, Attackers may fingerprint the server based on the information disclosed in error messages. Alternatively, attackers may attempt to trigger specific error messages to obtain technical information about the server. To avoid above situation, it is possible to configure the server to display generic, non-detailed error messages in the Apache Tomcat. Declare proper in web.xml wherein it is possible to specify the page which should be displayed on a certain Throwable/Expection/Error or a HTTP status code.


How to Do Avoid
===============

1) Build this code bases
2) Once it is build take the jar and drop it in <Carbon_Home>/repository/components/dropins/
3) Add these in <Carbon_Home>repository/conf/tomcat/carbon/WEB-INF/web.xml
```
    <error-page>
        <error-code>401</error-code>
        <location>/carbon/Error401.html</location>
    </error-page>
    <error-page>
        <error-code>403</error-code>
        <location>/carbon/Error403.html</location>
   </error-page>
   <error-page>
        <error-code>404</error-code>
        <location>/carbon/Error404.html</location>
  </error-page>
  <error-page>
        <error-code>405</error-code>
        <location>/carbon/Error405.html</location>
  </error-page>
  <error-page>
        <error-code>500</error-code>
        <location>/carbon/Error500.html</location>
  </error-page>
  <error-page>
        <exception-type>java.lang.Throwable</exception-type>
        <location>/carbon/ErrorLangThrowable.html</location>
  </error-page>
  <error-page>
        <exception-type>java.lang.Error</exception-type>
        <location>/carbon/ErrorLangError.html</location>
  </error-page>
  <error-page>
        <exception-type>java.lang.Exception</exception-type>
        <location>/carbon/ErrorLangException.html</location>
  </error-page>
```
4) Restart the server.


How to Do Test
===============
1) Try to access the https://localhost:8243/services/ or https://192.168.43.1:9443/wrong/mehtod/ssadasdasd.jsp
