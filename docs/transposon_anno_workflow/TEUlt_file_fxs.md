this is kind of dumb, but when I was troubleshooting through using TEUlt, it took me forever to figure out which specific scripts defined which steps of the pipeline, and which specific functions so here's a list lol
# AnnotationChecker.py
## functions
### getArgument
- inputs
	- args
	- title
- outputs
	- empty string

### getFile
- inputs
	- folder
	- suffix
- outputs
	- empty string
### checkHelitronScanner
- inputs
	- projectFolderPath
- output
	- True or False
### checkLtrHarvest
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkLtrPred
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkMiteFind
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkMiteTracker
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkMust
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkNCBIDD1000
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkRepeatModeler
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkRepeatMasker
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkSineFind
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkSineScan
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkTirVish
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkTransposonPSI
- inputs
	- projectFolderPath
- outputs
	- True or False
### checkAnnotations
- inputs
	- projectFolder, projectName
- outputs
	- listOkay
# AnnotationCommander
## functions
### getArgument 
- in: args, title
- out: empty string
### runHelitronScanner
- in: projectFolderPath
- out: runs Helitron Scanner
### runMust
- in: projectFolderPath, addCommand
- out: runs Must
### runMiteTracker
- in: projectFolderPath, addCommand
- out: runs mitetracker
### runTirVish
- in: projectFolderPath, addCommand
- out: runs tirvish