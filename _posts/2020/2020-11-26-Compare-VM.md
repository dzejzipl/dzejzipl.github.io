---
title: "PowerShell - compare-vm command"
categories:
    - PowerShell
tags:
    - PowerShell

header-img: "/assets/images/top_images/SynologyTOP.jpg"
subtitle:   "PowerShell - compare-vm command"
---
![PowerShell - compare-vm command](/assets/images/top_images/QuestionMarkTOP.jpg) What is a compare-vm command and how to use it?

I don't know if you know something like *Windows and Office deployment lab kit* but it is a complete lab for training about SCCM / Intune, etc. During lab initial setup I received the below error:

![PowerShell - compare-vm command](/assets/images/posts/compare-vm/01.png)

**Unable to import virtual machine due to configuration errors. Please use Compare-VM to repair the virtual machine**. Sounds familiar? Not for me. Let's see how to use that command and how to properly import VM to our environment.

1) Open PowerShell as administrator
2) Use command Compare-VM with *path* parameter to XML file of our affected VM.
![PowerShell - compare-vm command](/assets/images/posts/compare-vm/02.png)
3) And if you type: 
   ```powershell
   $compareVM.Incompatibilities.Message | Format-List
   ```
   You should receive a description of the issue. For me is:
   ![PowerShell - compare-VM command](/assets/images/posts/compare-vm/02.png)
   So, we have an issue that I don't have the required cores for this VM. 

It's all.
Now I know that I can change the number of cores before import and that should work!

Any questions? Just use the Disqus system to comment! :)
