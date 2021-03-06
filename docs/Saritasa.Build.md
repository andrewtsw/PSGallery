
# Saritasa.Build

## Copy-DotnetConfig

### Synopsis
Creates file from a template.

### Syntax
Copy-DotnetConfig \[-TemplateFilename\] &lt;String&gt; \[&lt;CommonParameters&gt;\]

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
			<td><nobr>TemplateFilename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to App.config.template or Web.config.template file.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Copy-DotnetConfig .\..\Web\Web.config.template

```
Creates a Web.config file in Web folder from template.

## Initialize-MSBuild

### Synopsis
Adds correct path to MSBuild to Path environment variable.

### Syntax
Initialize-MSBuild \[&lt;CommonParameters&gt;\]

## Install-NugetCli

### Synopsis
Downloads latest nuget.exe to specified location.

### Syntax
Install-NugetCli \[-Destination\] &lt;String&gt; \[&lt;CommonParameters&gt;\]

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
			<td><nobr>Destination</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td></td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Install-NugetCli .

```
Install nuget into current directory

## Invoke-EFMigrate

### Synopsis
Run Entity Framework migrations.

### Syntax
Invoke-EFMigrate \[-MigrationAssembly\] &lt;String&gt; \[\[-ConfigFilename\] &lt;String&gt;\] \[&lt;CommonParameters&gt;\]

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
			<td><nobr>MigrationAssembly</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to assembly file with migrations.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>ConfigFilename</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to assembly .config file. If not specified default or parent Web.config will be used.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
In essential this command tries to find migrate.exe in packages and run it against specified
configuration file.


### Examples
**EXAMPLE 1**
```
Invoke-EFMigrate ..\..\Domain\bin\Debug\Domain.dll

```
Runs all migrations declared in Domain.dll file, using Domain.dll.config as configuration file

## Invoke-NugetRestore

### Synopsis
Restores packages for solution, project or packages.config.

### Syntax
Invoke-NugetRestore -SolutionPath &lt;String&gt; \[&lt;CommonParameters&gt;\]

Invoke-NugetRestore -ProjectPath &lt;String&gt; -SolutionDirectory &lt;String&gt; \[&lt;CommonParameters&gt;\]

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
			<td><nobr>SolutionPath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to solution. All NuGet packages from included projects will be restored.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>ProjectPath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to project or packages.config.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>SolutionDirectory</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to the solution directory. Not valid when restoring packages for a solution.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
If nuget command is not found - it will be downloaded to current directory.


### Examples
**EXAMPLE 1**
```
Invoke-NugetRestore .\..\myapp.sln

```
Restores all packages for myapp solution.

## Invoke-ProjectBuild

### Synopsis
Builds project.

### Syntax
Invoke-ProjectBuild \[-ProjectPath\] &lt;String&gt; \[\[-Configuration\] &lt;String&gt;\] \[\[-Target\] &lt;String&gt;\] \[\[-BuildParams\] &lt;String\[\]&gt;\] \[&lt;CommonParameters&gt;\]

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
			<td>Path to project.</td>
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
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Target</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Build the specified targets in the project.  
Use a semicolon or comma to separate multiple targets.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg">Build</td>
		</tr>
		<tr>
			<td><nobr>BuildParams</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Additional build parameters.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
For more information about Target and BuildParams parameters, see MSBuild documentation.


### Examples
**EXAMPLE 1**
```
Invoke-ProjectBuild .\..\Web\Web.csproj -Configuration 'Release'

```


## Invoke-SolutionBuild

### Synopsis
Builds solution.

### Syntax
Invoke-SolutionBuild \[-SolutionPath\] &lt;String&gt; \[\[-Configuration\] &lt;String&gt;\] \[&lt;CommonParameters&gt;\]

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
			<td><nobr>SolutionPath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to solution.</td>
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
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Invoke-SolutionBuild .\..\myapp.sln -Configuration Debug

```


## Merge-PackageConfigs

### Synopsis
Loads packages from multiple packages.config and saves to a single file.

### Syntax
Merge-PackageConfigs \[-SolutionDirectory\] &lt;String&gt; \[-OutputPath\] &lt;String&gt; \[\[-Framework\] &lt;String&gt;\] \[&lt;CommonParameters&gt;\]

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
			<td><nobr>SolutionDirectory</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Directory in which to look for packages.config files.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>OutputPath</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Path to file in which results should be saved. If file exists, it will be overridden.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Framework</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>If specified, only packages with this framework will be included in the results.</td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Merge-PackageConfigs -SolutionDirectory .\src -OutputPath .\src\packages.merged.config

```

**EXAMPLE 2**
```
Merge-PackageConfigs -SolutionDirectory .\src -OutputPath .\src\packages.merged.net40.config -Framework net40

```
Merge-PackageConfigs -SolutionDirectory .\\src -OutputPath .\\src\\packages.merged.net452.config -Framework net452

## Update-AssemblyInfoFile

### Synopsis
Update version numbers of AssemblyInfo.cs and AssemblyInfo.vb.

### Syntax
Update-AssemblyInfoFile \[-Version\] &lt;String&gt; \[-WhatIf\] \[-Confirm\] \[&lt;CommonParameters&gt;\]

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
			<td><nobr>Version</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td>Version string in major.minor.build.revision format.</td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>WhatIf</nobr></td>
			<td class="visible-lg visible-md">wi</td>
			<td></td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Confirm</nobr></td>
			<td class="visible-lg visible-md">cf</td>
			<td></td>
			<td class="visible-lg visible-md">false</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Note
Based on SetVersion script.
http://www.luisrocha.net/2009/11/setting-assembly-version-with-windows.html
Copyright \(c\) 2009 Luis Rocha


### Examples
**EXAMPLE 1**
```
Update-AssemblyInfoFile '6.3.1.1'

```


## Update-VariablesInFile

### Synopsis
Replaces placeholders $\(UserName\) with values from hashtable.

### Syntax
Update-VariablesInFile \[-Path\] &lt;String&gt; \[-Variables\] &lt;Hashtable&gt; \[&lt;CommonParameters&gt;\]

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
			<td><nobr>Path</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td></td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
		<tr>
			<td><nobr>Variables</nobr></td>
			<td class="visible-lg visible-md"></td>
			<td></td>
			<td class="visible-lg visible-md">true</td>
			<td class="visible-lg">false</td>
			<td class="visible-lg"></td>
		</tr>
	</tbody>
</table>

### Examples
**EXAMPLE 1**
```
Update-VariablesInFile -Path Config.xml @{UserName='sa'}

```

