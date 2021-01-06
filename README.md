# lol-api-c3-plugin
Legends of Learning Plugin for Construct 3

This plugin features integration with Legends of Learning API integration for Construct 3. The plugin supports **C3 runtime only and worker mode**. C2 Runtime and Construct 2 is not supported and due to Construct 2 will soon be retired, there's no intention on developing a plugin for it.

The plugin not only provides you with API integration, but also with a couple of useful features like **multilang text manager** using the Get Text expression, **automatic highlight** using Set Highlight action, an action for **injecting your language file** to speed up your development using Set Lang From String action, **Mute/Unmute LoL voice** api, and **automatic** management of the game **progress submission**.

Please notice that this plugin is **distributed as Freeware**, This means the author retains all its copyrights rights, licensing, distribution, and modifications or derivated work from this plugin is prohibited. If you want to know more about the license, please visit the End User License Agreement for it. The EULA is also distributed and embedded within the plugin .c3addon file.

# Download Link
https://ppstudiomty.itch.io/lolapi-c3

# Documentation
https://www.imcsw.com/2020/12/07/legends-of-learning-api-integration/

# Issues, new features
In any case you have found a bug or a problem with the plugin, you may create an issue in this repository. To properly be able to help you, is important you submit the bug using the provided template.

https://github.com/sotano42/lol-api-c3-plugin/issues

# ACEs List in Alphabetic order

## Conditions
### Is Game Ready
Returns true if the LoL API has been initialized after calling GameIsReady action.

### On Correct Answer
After calling ShowQuestion action, is triggered when the player answers a LoL API question CORRECTLY.

### On Error
An error occurred during API calls. Use expression GetError for more details.

### On Incorrect Answer
After calling ShowQuestion action, is triggered when the player answers a LoL API question INCORRECTLY.

### On Load State
Triggered as callback from LoL API after action Load State is called. Here you can parse the payload returned and update your game state accordingly.

### On Pause
LoL API requested to Pause the game. Runtime is automatically suspended.

### On Resume
LoL API requested to Resume the game. Runtime is automatically resumed.

### On Save Completed
Triggered as callback from LoL API after action Save State action is called. If saving fails, then condition On Error will be triggered.

### On Start
Triggered when GameFrame reports to the game that it must start. You must call a GameIsReady action to report to the LoL GameFrame that your game is ready to be initialized.

## Actions
### Complete Game
Reports to LOL framework that player has finished the game

#### Game Is Ready
Report to LoL GameFrame that game is ready to receive data

#### Load State
Request to LoL API the state saved for the game. If it's successfully retrieved, then On Load State condition is triggered.

#### Mute LoL Voice
Prevents LoL API from speaking text, it doesn't stop audio playing

#### Reset Progress
Resets LoL game progress to zero. __Usefull for testing your game__. This action has no effect on your deployed project, so **please don't use it.**

#### Save State
Post and saves to LoL API the game state data

|Parameters|Description|
|-|-|
|Data|String containing the state; this can also be a strigified JSON.|

#### Set Highlight Color
Sets the color for highlighted words. To make the highlight work, you must add an key called 'highlight' on your language file, and it should contain a stringified array of strings. GetText expressions will look for every string and add a color code. A string can also be a regular expression string.

|Parameters|Description|
|-|-|
|Color|Color in hex format #999999 as a string.|

#### Set Lang From String
Sets the content of the language file from a string (use for testing only). Useful for testing without the LoL Test harness.

|Parameters|Description|
|-|-|
|Language|Language code. Eg. en, es, fr|
|Data|JSON lang file as a String|

#### Set Max Progress
Sets LoL Maximum game progress step.

|Parameters|Description|
|-|-|
|Max Progress|Max Progress value to submit (number).|

#### Show Question
Displays an overlay with a random LoL question.

#### Speak Text
Speaks a text string using LOL framework voice.

|Parameters|Description|
|-|-|
|Text Id|This id corresponds to the language file id assigned to the text|

#### Submit Auto Progress
Submits the game progress to LOL framework and handles the progress step count automatically. If Max Progress is reached, then no submission will be executed. Max Progress is defaulted to 8 steps. Use SetMaxProgress to modify it.

#### Submit Game Progress
Submits the game progress to LOL framework

|Parameters|Description|
|-|-|
|Progress|Submits the indicated progress step to LOL framework. Max Progress is defaulted to 8 steps. Use SetMaxProgress to modify it|

#### Suspend Runtime
Suspends the execution of the whole Construct runtime.

#### Unmute LoL Voice
Enables LoL API to speak text.

## Expressions

#### GetLastError
Returns the last error registered by the plugin

#### GetMaxProgress
Returns the maximum progress value expected for the game.

#### GetPayload
Returns the payload received from the LoL API as a string

#### GetProgress
Returns the current game progress.

#### GetRawText
Reads a string from the JSON language file

|Parameters|Description|
|-|-|
|Text ID|This id corresponds to the language file id assigned to the text.|

#### GetStateData
Returns the state data retrieved from LoL API

#### GetText
Reads a string from the JSON language file and applies the highlight

|Parameters|Description|
|-|-|
|Text ID|This id corresponds to the language file id assigned to the text.|

#### QuestionIndex
While looping using For Each Question, returns the QuestionIndex.

# Deprecated Features
The following ACEs had been deprecated in this plugin.

## Actions
#### Report Loading Progress *(Deprecated)*
Reports game loading progress to LOL framework

|Parameters|Description|
|-|-|
|Progress|Loading Progress value to submit to LoL Framework|

## Conditions
### For Each Alternative *(Deprecated)*
Loops every alternative available for the indicated QuestionIndex and updates the AlternativeIndex index-value. Use QuestionIndex in conjunction with AlternativeIndex expression to read specific fields of the alternative.

|Parameters|Description|
|-|-|
|Index|Question zero-based Index|

### For Each Question *(Deprecated)*
Loops every question available and updates the QuestionIndex index-value. Use QuestionIndex expression to read specific questions fields.

### Is Alternative Correct *(Deprecated)*
Tests wheter the indicated Alternative for the given Question is correct

|Parameters|Description|
|-|-|
|Index|Question zero-based Index|
|Alternative Index|Alternative zero-based Index|

### On Questions Ready *(Deprecated)*
Triggered after LoL GameFrame sends the questions back to your game.

## Expressions
#### AlternativeIndex *(Deprecated)*
While looping using For Each Alternative, returns the Alternative zero-based index for the question at QuestionIndex.

#### GetAlternativeChoiceNum *(Deprecated)*
Returns the alternative (answer) choice number for the question at QuestionIndex. This is the sequenced number LoL API assigns, it is NOT the zero-based index.

#### GetAlternativeId *(Deprecated)*
Returns the alternative (answer) unique ID for the question at QuestionIndex.

|Parameters|Description|
|-|-|
|Index|Alternative Index|

#### GetAlternativeText *(Deprecated)*
Returns the alternative (answer) text for the question at QuestionIndex

|Parameters|Description|
|-|-|
|Index|Alternative Index|

#### GetQuestionCorrectAltId *(Deprecated)*
Returns the unique Id of the correct alternative for the given question

|Parameters|Description|
|-|-|
|Question Index|Question zero-based Index|

#### GetQuestionCount *(Deprecated)*
Returns the number of questions retrieved from LoL API

#### GetQuestionId *(Deprecated)*
Returns the question unique Id

|Parameters|Description|
|-|-|
|Question Index|Question zero-based Index|

#### GetQuestionImageURL *(Deprecated)*
Returns a string containing the Image URL for the question. May return an empty string when there's no URL available.

|Parameters|Description|
|-|-|
|Question Index|Question zero-based Index|

#### GetQuestionStem *(Deprecated)*
Returns the question text.

|Parameters|Description|
|-|-|
|Question Index|Question zero-based Index|
