
# Saritasa.Publish

## Invoke-DatabaseProjectPublish

### Synopsis
Invoke build of database project and run migrations for database.

### Syntax
Invoke-DatabaseProjectPublish \[-ProjectPath\] &lt;String&gt; \[\[-Configuration\] &lt;String&gt;\] \[\[-Target\] &lt;String&gt;\] \[-ProfilePath\] &lt;String&gt; \[&lt;CommonParameters&gt;\]

### Parameters

<table class="table table-striped table-bordered table-condensed visible-on">
	<thead>
		<tr>
			<th>Name</th>
			<th class="visible-lg visible-md">Alias</th>
			<th>Description</th>
			<th class="visible-lg visible-md">Required?</th>
			<th class="visible-lg">Pipeline Input</th>
			<th class="visible-lg">Default Value</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><nobr>ProjectPath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to SQL Server database project.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Configuration</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Build configuration \(Release, Debug, etc.\)</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg">Release</td>
		</tr>
		<tr>
			<td><nobr>Target</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Build target \(Deploy, Publish, etc.\)</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg">Publish</td>
		</tr>
		<tr>
			<td><nobr>ProfilePath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to XML profile file.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Update-VariablesInFile -Path $profilePath -Variables @{ DatabasePassword = $DatabasePassword }

```
Invoke-DatabaseProjectPublish "$src\\Saritasa.Crm.Database\\Saritasa.Crm.Database.sqlproj" $Configuration -ProfilePath $profilePath -Target 'Build;Publish'  
Update password in build profile and run publish.
**EXAMPLE 2**
```
Invoke-DatabaseProjectPublish ..\src\MyApp.Database\MyApp.Database.sqlproj -ProfilePath ..\src\MyApp.Database\PublishProfiles\Production.publish.xml

```


## Invoke-FullPublish

### Synopsis
Publishes the ClickOnce application. Runs full publish: invoke project build and publish, set and update project's version.

### Syntax
Invoke-FullPublish \[-ProjectFilename\] &lt;String&gt; \[-PublishDir\] &lt;String&gt; \[\[-InstallUrl\] &lt;String&gt;\] \[\[-Version\] &lt;String&gt;\] \[\[-BuildParams\] &lt;String\[\]&gt;\] \[&lt;CommonParameters&gt;\]

### Parameters

<table class="table table-striped table-bordered table-condensed visible-on">
	<thead>
		<tr>
			<th>Name</th>
			<th class="visible-lg visible-md">Alias</th>
			<th>Description</th>
			<th class="visible-lg visible-md">Required?</th>
			<th class="visible-lg">Pipeline Input</th>
			<th class="visible-lg">Default Value</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><nobr>ProjectFilename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to project file to be published.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>PublishDir</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Directory to which the result application should be published.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>InstallUrl</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Location where users will install the application from  
\(see InstallUrl parameter description for msbuild cli for more information\).</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Version</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Version to be assigned to the application.  
If omitted, it will be automatically calculated by incrementing the revision number.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>BuildParams</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Additional build params to be passed for msbuild.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Invoke-FullPublish ..\src\myapp\myapp.csproj C:\publish\myapp -Version 4.4.2

```


## Invoke-ProjectBuildAndPublish

### Synopsis
Publishes the project and copies the publish.htm file to destination directory.

### Syntax
Invoke-ProjectBuildAndPublish \[-ProjectFilename\] &lt;String&gt; \[-PublishDir\] &lt;String&gt; \[\[-InstallUrl\] &lt;String&gt;\] \[\[-BuildParams\] &lt;String\[\]&gt;\] \[&lt;CommonParameters&gt;\]

### Parameters

<table class="table table-striped table-bordered table-condensed visible-on">
	<thead>
		<tr>
			<th>Name</th>
			<th class="visible-lg visible-md">Alias</th>
			<th>Description</th>
			<th class="visible-lg visible-md">Required?</th>
			<th class="visible-lg">Pipeline Input</th>
			<th class="visible-lg">Default Value</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><nobr>ProjectFilename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to project file to be published.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>PublishDir</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Directory to output the publish results.  
Will be cleared before publish.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>InstallUrl</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>InstallUrl property to be passed to MSBuild task.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>BuildParams</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Additional build params to be passed for MSBuild.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
publish.htm.template file should exist in the same directory where ProjectFilename file located.


## Set-ApplicationVersion

### Synopsis
Sets the ApplicationVersion information in a XML file.

### Syntax
Set-ApplicationVersion \[-Filename\] &lt;String&gt; \[-Version\] &lt;String&gt; \[&lt;CommonParameters&gt;\]

### Parameters

<table class="table table-striped table-bordered table-condensed visible-on">
	<thead>
		<tr>
			<th>Name</th>
			<th class="visible-lg visible-md">Alias</th>
			<th>Description</th>
			<th class="visible-lg visible-md">Required?</th>
			<th class="visible-lg">Pipeline Input</th>
			<th class="visible-lg">Default Value</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><nobr>Filename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>File path to process.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Version</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Version info to be set in ApplicationVersion item.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Set-ApplicationVersion ..\src\MyApp\MyApp.csproj 6.5.5

```


## Update-ApplicationRevision

### Synopsis
Updates the ApplicationRevision information a file by incrementing it and returns the updated revision value.

### Syntax
Update-ApplicationRevision \[-Filename\] &lt;String&gt; \[&lt;CommonParameters&gt;\]

### Parameters

<table class="table table-striped table-bordered table-condensed visible-on">
	<thead>
		<tr>
			<th>Name</th>
			<th class="visible-lg visible-md">Alias</th>
			<th>Description</th>
			<th class="visible-lg visible-md">Required?</th>
			<th class="visible-lg">Pipeline Input</th>
			<th class="visible-lg">Default Value</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><nobr>Filename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>File path to process.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
If ApplicationRevision information is not found in the file, the returned value will be 0.

