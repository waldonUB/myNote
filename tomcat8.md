### tomcat7变为tomcat8以后的版本,启动日志乱码的问题


**以前tomcat7的默认编码为IOS-8859-1,  
但到了tomcat8的Server.xml的编码已经默认为utf-8了  
无需再改,只需在tomcat8/conf/logging.properties中的**  
`*\apache-tomcat-8.5.37\conf\logging.properties增加
java.util.logging.ConsoleHandler.encoding = UTF-8

然后在idea  VM option加上 -Dfile.encoding=UTF-8

