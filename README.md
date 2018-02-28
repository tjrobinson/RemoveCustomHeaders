# Remove Custom Headers

Removes custom HTTP response headers for Azure App Service web applications including `Server`, `X-Powered-By`, `X-AspNet-Version` and `X-AspNetMvc-Version`.

https://www.nuget.org/packages/RemoveCustomHeaders

# How does it work?

This extension is just a simple wrapper over the following `ApplicationHost.xdt` file:

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
  <system.webServer>
    <httpProtocol>
      <customHeaders>
        <add xdt:Transform="Remove" />
      </customHeaders>
    </httpProtocol>
    <security>
      <requestFiltering removeServerHeader="true" xdt:Transform="SetAttributes(removeServerHeader)" />
    </security>
  </system.webServer>
</configuration>
```

These transform files are the supported way of allowing you to modify the default `ApplicationHost.config` file.
