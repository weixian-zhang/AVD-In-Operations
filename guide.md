1. Azure Image Builder or AIB builds new image version v1.1.0 from an existing base image v1.0.0
(could contain Windows Updates, azcopy App binary files, install server components and more)

2.	Switch On “Drain mode” for Session Hosts to stop new connections

3.	Logout users
a.	Send message to users
b.	wait for X minutes
c.	Logout users

4.	Remove existing Session Host - Get and loop through Session Hosts in Host Pool and remove Session Host
(If there an any in-place upgrade technique without removal please let us know)

5.	Add Session Host with image from Compute Gallery image v1.1.0

- using ARM template
https://github.com/hardeights/RDS-Templates/blob/master/wvd-templates/Create%20and%20provision%20WVD%20host%20pool/mainTemplate.json  

- using Bicep  
https://rbnmk.net/2021/08/09/using-biceps-loadtextcontent-for-azure-image-builder/
https://github.com/rbnmk/bicep-loadcontent-image-builder/blob/main/example/vm-jumphost-deployment.bicep

  -blog 2:
   https://github.com/jamesatighe/AVD-BICEP


   AIB definition
     - arm
     https://github.com/Azure/azvmimagebuilder/blob/main/quickquickstarts/2_Creating_a_Custom_Win_Shared_Image_Gallery_Image_from_SIG/helloImageTemplateforSIGfromWinSIG.json

     - bicep  
     https://github.com/rbnmk/bicep-loadcontent-image-builder/blob/975a4dd5bfba83d00c25ae51c6b642de73c12d8b/modules/vm-image-template-pwsh.bicep

 

6.	Test new v1.1.0 by signing in to new Session Host before releasing to users
