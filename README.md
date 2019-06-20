# Anki JavaScript Cards

This demonstrates one method for creating JavaScript based Anki cards.

Tested on
 * [Anki for desktop computers][anki-desktop] version 2.1.13
 * [AnkiMobile][anki-mobile] (iOS) version 2.0.48

## Instructions

1. Ensure you have synchronized all your Anki clients
1. Open Anki for desktop computers
1. Click _Create Deck_
1. Enter `Test` for the desk name and click _OK_
1. Click the `Test` deck
1. Click `Add`
1. Click the _Type_ button
1. Click _Manage_ → _Add_
1. Select _Clone: Basic_ and click _OK_
1. Enter `Script` for _Name_ and click _OK_
1. Close the window
1. Select _Script_ and click _Choose_
1. Click _Cards..._
1. Enter the following for _Front Template_:
   ``` javascript
   <div id="front" class="card">Loading front...</div>

   <script>
   var code = (function () {/* {{Front}} */}).toString();
   code = code.slice(16, code.length - 4);
   eval(new DOMParser().parseFromString(code, "text/html").documentElement.textContent);
   </script>
   ```
   _NOTE: You can ignore the "Invalid HTML on card: ReferenceError: Front is not defined" error._
1. Enter the following for _Back Template_ (ignore the "Invalid HTML on card: ReferenceError: Back is not defined" error):
   ``` javascript
   <div id="back" class="card">Loading back...</div>
   
   <script>
   var code = (function () {/* {{Back}} */}).toString();
   code = code.slice(16, code.length - 4);
   eval(new DOMParser().parseFromString(code, "text/html").documentElement.textContent);
   </script>
   ```
   _NOTE: You can ignore the "Invalid HTML on card: ReferenceError: Back is not defined" error._
1. Click _Close_
1. Enter the following for _Front_:
   ``` javascript
   window.now = new Date();

   document.getElementById('front').innerHTML = 'What is the current year?';
   ```
1. Enter the following for _Back_:
   ``` javascript
   document.getElementById('back').innerHTML = 'Current year: ' + window.now.getFullYear();
   ```
1. Click _Add_
1. Click _Close_
1. Click _Study Now_ → _Show Answer_

[anki-desktop]: https://apps.ankiweb.net
[anki-mobile]: https://apps.apple.com/us/app/ankimobile-flashcards/id373493387