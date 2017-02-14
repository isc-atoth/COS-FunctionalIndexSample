# Functional index samples
Sample implementations of InterSystems Caché's Funtional Index feature

This project contains some sample implementations of the [Functional Index](http://docs.intersystems.com/latest/csp/documatic/%25CSP.Documatic.cls?APP=1&LIBRARY=%25SYS&CLASSNAME=%25Library.FunctionalIndex) feature of [InterSystems](http://www.intersystems.com) Caché and Ensemble. As well as simple REST interfaces and web-applications for testing purposes.

Questions, bug reports, recommendations are highly welcome to Attila.Toth@InterSystems.com

### Installation
- Download and extract the project to a directory (\<install-dir\>).
- Choose one or more from the available samples, then import and compile all the XML files belonging to your selected samples onto one of your Caché / Ensemble namespaces.
- Execute the installer, which comes with the selected sample to make sure everything is installed and configured properly (*).
- Populate sample data into the appropriate **Data** class (either by inserting records from the object/SQL interface or by using the *Populate()* utility).

Example: 
```
Do $System.OBJ.LoadDir("<install-dir>/v1-SimpleIndex","c",.err,1,.list)
Set pVars("RESTUrl")="/fulltext"	; optional: defaults to "/fulltext"
Do ##class(fulltext.search.v1.Installer).setup(.pVars)
Write ##class(fulltext.search.v1.Data).Populate(100000)
```

#### (*) Installation notes
- The project always installs on your current namespace!
- The installer will try to find a CSP Application configuration for the related REST interface. The application name defaults to */fulltext*. To change this, see the code snippet above! If the specified CSP Application doesn't exist, the installer will automatically create it.
- If you choose a name for the REST CSP Application other than "/fulltext", you will have to go to the **fulltext.search.REST** class and edit its **LOCATION** class parameter accordingly!
- The installer doesn't create a CSP Application for the sample web-application! If you need one (for example: your current namespace has no default CSP Application), please create one for your namespace manually! (For help, see the [Online Documentation](http://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=GCSP_config_server#GCSP_config_newapp)) 

### Usage
Either open the attached sample web-application or browse the source code and class documentations for additional details.
The sample UI uses some external JavaScript libraries from the Internet. So either you'll need Internet access or download the appropriate libraries to your local filesystem and change the **fullTextSearch.csp** accordingly!

### Version history
- 1.0: Initial version - Simple functional index, supporting [%INSET](http://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RSQL_inset) only.