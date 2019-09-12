# cdToolboxVue
Vue Components and Documentation for the CDToolbox

## Components
### JobClient
The Job-Client Component contains the jobnumber, clientname, and subjobs for a job number.
Use:
Import the component
`import JobClient from '../common/JobClient';`
Add the component to the list of components
```
components:{
  JobClient
}
```
Add the component to the HTML
```
<JobClient
  v-on:dataUpdated="getJobInfo"
/>
```
The v-on:dataUpdated="getJobInfo" is a function that is called everytime something is inputted into the textbox.
The function "getJobInfo" handles the data the component passes up to it.
In your methods section, add the "getJobInfo" function
```
methods: {
  getJobInfo: function(data){
    //data is an object that contains the subjobs, clientname, and jobnumber
    console.log(data);
    //output would be {subjobs:[], clientname: "", jobnumber: "")
    //with different values for the items inside
  }
}
```

### SubLOB
The Sub-LOB Component contains the subjob, lob, and pkgs for a subjob.
Use:
Import the component
`import SubLOB from '../common/SubLOB';`
Add the component to the list of components
```
components:{
  SubLOB
}
```
Add the component to the HTML
```
<SubLOB 
  v-on:dataUpdated="getSubJobInfo"
  :subjobs="subjobs"
  :jobnumber="jobnumber"
/>
```
The v-on:dataUpdated="getSubJobInfo" is a function that is called everytime the subjob changes.
The function "getSubJobInfo" handles the data the component passes up to it.
In your methods section, add the "getSubJobInfo" function
```
methods: {
  getSubJobInfo: function(data){
    //data is an object that contains the subjob, lob, and pkgs
    console.log(data);
    //output would be {subjob: "", lob: "", pkgs: [])
    //with different values for the items inside
  }
}
```
The :subjobs="subjobs" is the list of subjobs the component can use that we pass into the component.
In your data section, add the "subjobs" array
```
data: () => ({
  subjobs: [] //this should be filled out by the JobClient component
  //whenever subjobs changes, the subjobs in the dropdown will change
})
```
The :jobnumber="jobnumber" is the jobnumber the component can use that we pass into the component.
In your data section, add the "jobnumber" string
```
data:() => ({
  jobnumber: "" //This is used to grab the LOB, and should be provided by the JobClient Component
});
```

### Pkg
The Pkg Component contains the selected packages.
Use:
Import the component
`import Pkg from '../common/Pkg';`
Add the component to the list of components
```
components:{
  Pkg
}
```
Add the component to the HTML
```
<Pkg 
  v-on:dataUpdated="getPkgInfo"
  :pkgs="pkgs"
  :multiplePkgs="multiplePkgs"
/>
```
The v-on:dataUpdated="getPkgInfo" is a function that is called everytime the packages change.
The function "getPkgInfo" handles the data the component passes up to it.
In your methods section, add the "getJobInfo" function
```
methods: {
  getPkgInfo: function(data){
    //data is an object that contains the selected pkgs
    console.log(data);
    //output would be {pkgs: [])
    //with different values for the item inside
  }
}
```
The :pkgs="pkgs" is the list of pkgs the component can use that we pass into the component.
In your data section, add the "pkgs" array
```
data: () => ({
  pkgs: [] //this should be filled out by the SubClient Component
  //Whenever pkgs changes, the pkgs in the dropdown also changes
})
```
The :multiplePkgs="multiplePkgs" is an optional simple true/false variable if the component should allow multiple package selection or not.
You can directly put "true" or "false" instead of multiplePkgs to achieve the needed effect
```
:multiplePkgs="true" //now we can enter one to many packages
:multiplePkgs="false" //now we can only have one pkg

//False is the Default if this isn't passed
```

### CycleNumber
The Cycle-Number Component contains the selected cyclenumbers for a job number.
Use:
Import the component
`import CycleNumber from '../../common/CycleNumber';`
Add the component to the list of components
```
components:{
  CycleNumber
}
```
Add the component to the HTML
```
<CycleNumber
  v-on:dataUpdated="getCycleDetails"
 	:jobnumber="jobnumber"
 	:multipleCycles="multipleCycles"
/>
```
The v-on:dataUpdated="getCycleDetails" is a function that is called everytime the Cycle Number changes.
The function "getCycleDetails" handles the data the component passes up to it.
In your methods section, add the "getCycleDetails" function
```
methods: {
  getCycleDetails: function(data){
    //data is an object that contains the selected cyclenumbers
    console.log(data);
    //output would be {cycleNumbers: [])
    //with different values for the items inside
  }
}
```
The :jobnumber="jobnumber" is the jobnumber the component can use that we pass into the component.
In your data section, add the "jobnumber" string
```
data:() => ({
  jobnumber: "" //This is used to grab the valid cycle numbers, and should be provided by the JobClient Component
});
```
The :multipleCycles="multipleCycles" is an optional simple true/false variable if the component should allow multiple cycle numbers selection or not.
You can also directly put "true" or "false" instead of multipleCycles to achieve the needed effect
```
:multipleCycles="true" //now we can enter one to many cycle numbers
:multipleCycles="false" //now we can only have one cycle number

//False is the Default if this isn't passed
```

### JobSubClientLob
The Job-Sub-Client-Lob Component contains the jobnumber, clientname, subjob, and lob for the given jobnumber and subjob.
This component is a premade collection of the JobClient and SubLOB components.
Use:
Import the component
`import JobSubClientLob from '../../common/JobSubClientLob';`
Add the component to the list of components
```
components:{
  JobSubClientLob
}
```
Add the component to the HTML
```
<JobSubClientLob 
	v-on:dataUpdated="getJobSubClientLobDetails"
/>
```
The v-on:dataUpdated="getJobSubClientLobDetails" is a function that is called everytime the jobnumber or subjob changes.
The function "getJobSubClientLobDetails" handles the data the component passes up to it.
In your methods section, add the "getJobSubClientLobDetails" function
```
methods: {
  getJobSubClientLobDetails: function(data){
    //data is an object that contains the subjob, clientname, lob, and jobnumber
    console.log(data);
    //output would be {lob: "", subjob: "", clientname: "", jobnumber: "")
    //with different values for the items inside
  }
}
```

### JobSubClientLobPkg
The Job-Sub-Client-Lob-Pkg Component contains the jobnumber, clientname, subjob, lob, and package for the given jobnumber and subjob.
This component is a premade collection of the JobClient, SubLOB, and Pkg components.
Use:
Import the component
`import JobSubClientLobPkg from '../../common/JobSubClientLobPkg';`
Add the component to the list of components
```
components:{
  JobSubClientLobPkg
}
```
Add the component to the HTML
```
<JobSubClientLobPkg
  v-on:dataUpdated="getJobSubClientLobPkgDetails"
 	:multiplePkgs="true"  	
/>
```
The v-on:dataUpdated="getJobSubClientLobPkgDetails" is a function that is called everytime the jobnumber, subjob, or pkg changes.
The function "getJobSubClientLobPkgDetails" handles the data the component passes up to it.
In your methods section, add the "getJobSubClientLobPkgDetails" function
```
methods: {
  getJobSubClientLobPkgDetails: function(data){
    //data is an object that contains the subjob, clientname, lob, pkg, and jobnumber
    console.log(data);
    //output would be {lob: "", subjob: "", clientname: "", jobnumber: "", pkg: [])
    //with different values for the items inside
  }
}
```
The :multiplePkgs="multiplePkgs" is an optional simple true/false variable if the component should allow multiple package selection or not.
You can directly put "true" or "false" instead of multiplePkgs to achieve the needed effect
```
:multiplePkgs="true" //now we can enter one to many packages
:multiplePkgs="false" //now we can only have one pkg

//False is the Default if this isn't passed
```
### FileSelection
The File-Selection Component allows the user to select from a list of pre-defined files.
Use:
Import the component
`import FileSelection from '../../common/FileSelection';`
Add the component to the list of components
```
components:{
  FileSelection
}
```
Add the component to the HTML
```
<FileSelection
  v-on:dataUpdated="getFileSelectionDetails"
	:files="files"
	:multipleFiles="true"
	:key="fileselkey"
/>
```

### FileBrowser
The File-Browser Component allows the user to select a file
Use:
Import the component
`import FileBrowser from '../../common/FileBrowser';`
Add the component to the list of components
```
components:{
  FileBrowser
}
```
Add the component to the HTML
```
<FileBrowser
  v-on:dataUpdated="getFileBrowserDetails"
	:multipleFiles="multipleFiles"
	:browselabel="'Select File'"
/>
```

The v-on:dataUpdated="getFileBrowserDetails" is a function that is called everytime the selected file changes.
The function "getFileBrowserDetails" handles the data the component passes up to it.
In your methods section, add the "getFileBrowserDetails" function
```
methods: {
  getFileBrowserDetails: function(data){
    //data is an object that contains the selected files
    console.log(data);
    //output would be {files: [])
    //with different values for the item inside
  }
}
```
The :multipleFiles="multipleFiles" is an optional simple true/false variable if the component should allow multiple file selection or not.
You can directly put "true" or "false" instead of multipleFiles to achieve the needed effect
```
:multipleFiles="true" //now we can select one to many files
:multipleFiless="false" //now we can only have one file

//False is the Default if this isn't passed
```
The :browselabel="'Select Client Data File'" is a required string the component uses to display to the user.
You can pass a string variable, or pass a literal string through by surrounding it in apostrophes.

### Fields

### ConfigLoader

### RunButton

## Creating a new tool
Create .vue file using the following skeleton.

```
<template>
 <v-app>
 <!-- Progress bar to let the user know something is running -->
 <v-progress-linear
   indeterminate
   color="primary"
   v-show="loading"
 ></v-progress-linear>
  <!-- alert messages, for when a job is done -->
  <v-alert
   dismissible
   v-for="(item, i) in runningJobs"
   v-model="item.showalert"
   :type="item.alerttype"
   >
   {{item.status}}
</v-alert>


<!-- Run Button and Clear Button -->
<span style="float:right;">
 <RunButton
   :runData="runData"
  v-on:progressUpdated="getRunStatus"
  />
  <v-btn
    color="error"
      class="mr-4"
      @click="resetForm"
    >
     Clear
   </v-btn>
   </span>
   </v-app>
</template>
<script>
import RunButton from '../../common/RunButton';
export default {
 props: ['compKey'],
 components:{
   RunButton
 },
 data: () => ({
   runData: {runningTool:""}, //this gets passed to the run button
   runningJobs: [],  //So we know what's running
   loading: false   //lets the toolbox know something is running
 }),
 methods: {
   getRunStatus: function(data){
    //console.log(data);
    this.loading = data.loading;
    this.emitProgress(data.loading ? "loading" : "done");
    this.runningJobs = get_cdtlb().getAlerts(data.igniteData, this.runData.runningTool);
  },
  emitProgress: function(progress){
  	var content = {
 	  progress: progress,
   	  key: this.compKey
  	}
  	console.log([progress,content]);
  	this.$emit("progressUpdated", content);
    }
  },
  mounted: function() { //Mounted = tool is ready
    this.emitProgress("done");
  }
}
</script>
```
Update the tools.json file
```
{
      "id": One Higher than the last,
      "name": "Tool Name",
      "hidden": true,
      "description": "Tool Description",
      "Version": "0.1.0",
      "Group": "Tool Group",
      "category": "enter category"
      "Updates": [],
      "Component": "Enter component name with no spaces - NewTool in this case"
    }
```

Update the cdtoolbox.vue file
```
//import the vue file
import NewTool from './tools/cd/NewTool';
```
Add to the components list
```
components:{
 ...,
 NewTool,
 ...
}
```
Add to the getValidTools else if line
```
else if (this.tools[t].name == "Tool Name")
 {
 this.visibletools.push(this.tools[t]);
}
```
