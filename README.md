# Probitok.com-Collector
This is a IMacros Script that collects Bitcoin every two minutes from http://probitok.com .

VERSION BUILD=8970419 RECORDER=FX
SET !TIMEOUT_TAG 30
SET !TIMEOUT_STEP 30
SET !TIMEOUT_PAGE 30
SET !REPLAYSPEED FAST 
TAB CLOSEALLOTHERS 
SET !EXTRACT_TEST_POPUP NO 
SET !ERRORIGNORE YES
SET !DATASOURCE_LINE {{!LOOP}}
SET !VAR1 1FgtZf6TRyWX9NdrzMLe7dbi5Pcn5seggH
SET !VAR2 5877b17ca887d0a6e6f9da52ad1f94aHgg                 
SET !VAR3 C:\Users\spectre\Documents\iMacros\Captcha\Capture.jpg

TAB T=1
URL GOTO=http://probitok.com/?r=18VpyALCSBifx4osbG5dCw6izdiAL5KeyX
WAIT SECONDS=5
TAG POS=1 TYPE=INPUT:TEXT FORM=ID:submitForm ATTR=NAME:BwDFhL1vs683yDS1DRXmkJ36olfQ3P2gQQO CONTENT={{!VAR1}}
WAIT SECONDS=5
TAG POS=1 TYPE=IMG ATTR=ID:adcopy-puzzle-image-image
WAIT SECONDS=5
ONDOWNLOAD FOLDER=C:\Users\spectre\Documents\iMacros\Captcha FILE=Capture.jpg WAIT=YES
WAIT SECONDS=1
TAG POS=1 TYPE=IMG ATTR=ID:recaptcha_challenge_image CONTENT=EVENT:SAVE_ELEMENT_SCREENSHOT
TAB OPEN
TAB T=2
URL GOTO=https://2captcha.com/imacros.html
TAG POS=1 TYPE=INPUT:TEXT FORM=ACTION:http://rucaptcha.com/in.php ATTR=NAME:key CONTENT={{!VAR2}}
TAG POS=1 TYPE=INPUT:FILE FORM=ACTION:http://rucaptcha.com/in.php ATTR=NAME:file CONTENT={{!VAR3}}
ONDIALOG POS=1 BUTTON=OK CONTENT=
TAG POS=1 TYPE=INPUT:SUBMIT FORM=ACTION:http://rucaptcha.com/in.php ATTR=*
TAG POS=1 TYPE=INPUT:SUBMIT ATTR=TYPE:submit&&VALUE:recognize
WAIT SECONDS=2
SET !EXTRACT NULL
TAG POS=1 TYPE=* ATTR=TXT:* EXTRACT=TXT
WAIT SECONDS=1
TAB CLOSE
SET !VAR6 EVAL("if (\"{{!EXTRACT}}\" == \"#EANF#\") {var x = \"\";} else {var x = \"{{!EXTRACT}}\";} x;")
SET !EXTRACT NULL
TAG POS=1 TYPE=INPUT:TEXT FORM=ID:submitForm ATTRID:adcopy_response CONTENT={{!VAR6}}
WAIT SECONDS=3
TAG POS=1 TYPE=IMG ATTR=SRC:http://probitok.com/templates/purplehome/images/presssubmitbutton.png
WAIT SECONDS=120
