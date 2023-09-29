---
content_type: page
description: ''
learning_resource_types:
- Lecture Notes
ocw_type: CourseSection
parent_title: Lecture Notes
parent_type: CourseSection
parent_uid: 4820948e-86a5-7932-49d2-2b7a99eed7a6
title: 'Appendix 2: Praat Script to Load Multiple Files'
uid: 23af36f9-11eb-a169-a7ec-9008b53165b7
---

Chapters: {{% resource_link 63b36342-5b94-361a-cbe3-ced6adf82df1 "1.0" %}} | {{% resource_link fc91f34c-76a7-b6cc-b829-38198fe64b46 "2.0" %}} | {{% resource_link 3dfd44c5-aed7-88ee-d755-97256ba0108f "2.1" %}} | {{% resource_link 7a026ab3-478e-eee9-8f88-16e1e90d1654 "2.2" %}} | {{% resource_link f7dc6299-c37b-c75d-a6b6-21e8f0992078 "2.3" %}} | {{% resource_link 25ee8afa-dae8-7121-db12-81326f2f65f1 "2.4" %}} | {{% resource_link 1d1bf60f-d4a9-a667-05e4-c11ecf39f7b3 "2.5" %}} | {{% resource_link ead3994f-79d8-efce-de8c-910eda239315 "2.6" %}} | {{% resource_link ab88cf98-157e-98cf-adfc-7acb78ec06d1 "2.7" %}} | {{% resource_link 2cac7be1-bd58-1270-4fc9-d84c270a9cff "2.8" %}} | {{% resource_link 2fbd2615-f2f0-7541-5bda-027626b5ad45 "2.9" %}} | {{% resource_link a92606a9-0f30-6b31-378d-e45e4989e61a "2.10" %}} | {{% resource_link 10c2e8c0-3657-28bc-5548-98ac5f52bd72 "2.11" %}} | {{% resource_link dff3a4e9-f103-de11-edc1-a823ddd8c48b "2.12" %}} | {{% resource_link 966177a5-5ddb-0185-a762-33f4bebd02d2 "Appendix 1" %}} | Appendix 2

#OpenToBI

\# This script prompts for a list of file name, and opens each .wav  
\# file corresponding .TextGrid files from a specified directory.

tobidir$ = "."  
examples$ = "tobi\_examples"

clearinfo

form Open .wav and text grid  
text file\_list  
endform

while length(file\_list$) > 0  
list\_length = length(file\_list$)  
firstspace = index(file\_list$, " ")  
if firstspace = 0  
file\_name$ = file\_list$  
file\_list$ = ""  
else  
file\_name$ = left$(file\_list$,firstspace-1)  
file\_list$ = mid$(file\_list$,firstspace+1,list\_length-firstspace)  
endif

sound\_file$ = tobidir$+"/"+examples$+"/"+file\_name$+".wav"  
if fileReadable(sound\_file$)  
Read from file... 'sound\_file$'  
else  
printline 'sound\_file$' is not readable  
endif

text\_file$ = tobidir$+"/"+examples$+"/"+file\_name$+".TextGrid"  
if fileReadable(text\_file$)  
Read from file... 'text\_file$'  
else  
printline 'text\_file$' is not readable  
endif  
endwhile