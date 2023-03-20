# Demo of jetty-web.xml processing
this demo shows that since GWT 2.10.0 the processing of the jetty-web.xml does not work as described in the [Jetty 9.4 documentation](https://www.eclipse.org/jetty/documentation/jetty-9/index.html#jetty-web-xml-config).

## how to demo
1. import this project into IntelliJ IDEA.
2. execute the provided run configuration Demo

As result on the console jetty fails to configure the WebAppContext.
This works with GWT 2.9.0 or when we build a war and deploy it in Jetty 9.4

    java.lang.ClassNotFoundException: org.eclipse.jetty.webapp.WebAppContext
    at java.lang.ClassLoader.findClass(ClassLoader.java:523)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
    at org.eclipse.jetty.webapp.WebAppClassLoader.loadClass(WebAppClassLoader.java:487)
    at com.google.gwt.dev.shell.jetty.JettyLauncher$WebAppContextWithReload$WebAppClassLoaderExtension.loadClass(JettyLauncher.java:458)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
    at org.eclipse.jetty.util.Loader.loadClass(Loader.java:64)
    at org.eclipse.jetty.xml.XmlConfiguration$JettyXmlConfiguration.nodeClass(XmlConfiguration.java:477)
    at org.eclipse.jetty.xml.XmlConfiguration$JettyXmlConfiguration.configure(XmlConfiguration.java:417)
    at org.eclipse.jetty.xml.XmlConfiguration.configure(XmlConfiguration.java:364)
    at org.eclipse.jetty.webapp.JettyWebXmlConfiguration.lambda$configure$0(JettyWebXmlConfiguration.java:94)
    at org.eclipse.jetty.webapp.WebAppClassLoader.runWithServerClassAccess(WebAppClassLoader.java:138)
    at org.eclipse.jetty.webapp.JettyWebXmlConfiguration.configure(JettyWebXmlConfiguration.java:92)
    at org.eclipse.jetty.webapp.WebAppContext.configure(WebAppContext.java:498)
    at org.eclipse.jetty.webapp.WebAppContext.startContext(WebAppContext.java:1409)
    at org.eclipse.jetty.server.handler.ContextHandler.doStart(ContextHandler.java:910)
    at org.eclipse.jetty.servlet.ServletContextHandler.doStart(ServletContextHandler.java:288)
    at org.eclipse.jetty.webapp.WebAppContext.doStart(WebAppContext.java:524)
    at com.google.gwt.dev.shell.jetty.JettyLauncher$WebAppContextWithReload.doStart(JettyLauncher.java:568)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start(AbstractLifeCycle.java:73)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.start(ContainerLifeCycle.java:169)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.doStart(ContainerLifeCycle.java:110)
    at org.eclipse.jetty.server.handler.AbstractHandler.doStart(AbstractHandler.java:97)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start(AbstractLifeCycle.java:73)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.start(ContainerLifeCycle.java:169)
    at org.eclipse.jetty.server.Server.start(Server.java:423)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.doStart(ContainerLifeCycle.java:110)
    at org.eclipse.jetty.server.handler.AbstractHandler.doStart(AbstractHandler.java:97)
    at org.eclipse.jetty.server.Server.doStart(Server.java:387)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start(AbstractLifeCycle.java:73)
    at com.google.gwt.dev.shell.jetty.JettyLauncher.start(JettyLauncher.java:776)
    at com.google.gwt.dev.DevMode.doStartUpServer(DevMode.java:636)
    at com.google.gwt.dev.DevModeBase.startUp(DevModeBase.java:898)
    at com.google.gwt.dev.DevModeBase.run(DevModeBase.java:705)
    at com.google.gwt.dev.DevMode.main(DevMode.java:432)
    Suppressed: java.lang.ClassNotFoundException: org.eclipse.jetty.webapp.WebAppContext
    at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
    at org.eclipse.jetty.webapp.WebAppClassLoader.findClass(WebAppClassLoader.java:629)
    at org.eclipse.jetty.webapp.WebAppClassLoader.loadClass(WebAppClassLoader.java:511)
    ... 31 more



