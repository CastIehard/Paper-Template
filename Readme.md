Add this line to user settings.json to put all temporary files into temp:

   ```json
   {
     "dart.flutterSdkPath": "C:\\ProgramData\\flutter",
     "cmake.showOptionsMovedNotification": false,
     "git.autofetch": true,

     // LaTeX Workshop configuration
     "latex-workshop.latex.tools": [
       {
         "name": "latexmk",
         "command": "latexmk",
         "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "-pdf",
           "-auxdir=./temp",  // Stores auxiliary files in "temp"
           "-outdir=./temp",  // All output files in "temp" temporarily
           "%DOC%"
         ]
       },
       {
         // Custom command to move the PDF from temp to the root directory
         "name": "move-pdf",
         "command": "powershell",
         "args": [
           "Move-Item",
           "./temp/%DOCFILE%.pdf",
           "./%DOCFILE%.pdf"
         ]
       }
     ],
     "latex-workshop.latex.recipes": [
       {
         "name": "latexmk",
         "tools": [
           "latexmk",
           "move-pdf"  // This moves the PDF from temp to the root folder
         ]
       }
     ]
   }
   ```