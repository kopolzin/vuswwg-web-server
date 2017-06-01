[Return to Table of Contents](README.md)
### Default database location
The default database file for Blazegraph is located at `/opt/tomcat/temp/bigdata.jnl`.

You may wish to back up this file or monitor its size when loading large datasets.

### Modify the Blazegraph GUI
Edit `/opt/tomcat/webapps/bg/html/index.html`, where "bg" is the context name given to Blazegraph in Jelastic. Comment out the following sections like so (look for the \<!-- and --\>):
```
<td width = "20%" border = "0" align = "right" valign = "middle" id = "nopad">
    <!--form id="search-form"><label for="search-text">SEARCH:</label> <input type="text" id="search-text"><button type="submit"><span>&nbsp;</span></button></form-->
</td>
```
```
<div id="tab-selector">
    <!--a data-target="splash" class="active">Welcome</a-->
    <a data-target="query">Query</a>
    <!--a data-target="update">Update</a-->
    <a data-target="explore">Explore</a>
    <!--a data-target="namespaces">Namespaces</a>
    <a data-target="status">Status</a>
    <a data-target="health">Health</a>
    <a data-target="performance">Performance</a-->
    <p>Current namespace: <span id="current-namespace"></span></p>
</div>
```

To further customize the GUI you may edit other files in the `/opt/tomcat/webapps/bg/html/` directory.
