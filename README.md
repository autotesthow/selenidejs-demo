# Demo of browser automation with SelenideJs

This [code in JavaScript](https://github.com/autotesthow/selenidejs-demo) comes from the «Browser Automation Demo» lesson as part of the [Quality Engineer (or SDET) Learning Map](http://autotest.how/map). To get consulted on your own learning path, pass the following quiz, available in:

* [ukrainian](https://forms.gle/gjQLK8geTtndmdx76)
* [russian](https://forms.gle/TJp9EZubqcLf4p3K6)
* english (coming soon)

## Video Recordings

* [Version in Russian](https://www.loom.com/share/b521ce3df4704825bb4030388f358d78)
* Version in English: TODO
* Version in Ukrainian: (coming soon)

## Other code versions from this demo

* [Java](https://github.com/autotesthow/jselenide-demo)
* [Python](https://github.com/autotesthow/selene-demo)

## Prerequisites

* [NodeJs](https://nodejs.org/en/download/current/)
* [Chrome Browser](https://www.google.com/chrome/)
* [Visual Studio Code](https://code.visualstudio.com/)
  * you must install also the «code» command to run the editor directly from the terminal: when opened Visual Studio Code, in the Menu «View» -> «Command Palette» (Ctrl+Shift+P on Windows or Command+Shift+P on Mac) type «shell command» and select «install 'code' command in Path» and press Enter

## Instructions

### To repeat the demo yourself

Ensure you installed everything from the Prerequisites section.

Open the unix terminal (you can install [Git](https://git-scm.com/) and open a «git bash» on Windows) and execute the following commands (just copy&paste everything into the terminal and press Enter):

```bash
mkdir selenidejs-demo \
&& cd $_ \
&& npm init -y \
&& node -e "require('fs').writeFileSync('./package.json', JSON.stringify({type: 'module', ...require('./package.json'), license: 'MIT'}, null, 2))" \
&& npm install --save-dev selenidejs chromedriver geckodriver \
&& echo '{
  "compilerOptions": {
    "allowJs": true,
    "maxNodeModuleJsDepth": 1,
    "checkJs": true,
    "noEmit": true,
    "target": "ES2022",
    "module": "ES2022",
    "moduleResolution": "node16"
  },
  "include": [
    "./**/*.*"
  ]
}' > tsconfig.json \
&& code .

```

In the opened Visual Studio Code, create a new file «google-finds-selenide.js» and paste the following code:

```javascript
import 'chromedriver'
import { browser, have } from 'selenidejs'

await browser.open('https://google.com/ncr')
await browser.element('[name=q]').type('selenidejs')
await browser.element('[name=q]').pressEnter()

await browser.all('#rso>div').should(have.size(9))
await browser.all('#rso>div').first.should(have.text('SelenideJS - GitHub'))
await browser.all('#rso>div').first.element('h3').click()

await browser.should(have.titleContaining('GitHub - KnowledgeExpert/selenidejs'))

await browser.quit()
```

Come back to the terminal or open a new one inside Visual Studio Code by pressing Ctrl+Shift+\` on windows or Command+Shift+\` on Mac, and execute the following command:

```bash
node google-finds-selenide.js
```

Enjoy the result!

P.S.
You may find that your google search results are different from the ones in the video. This is because Google is constantly changing its search algorithm. So, if you see different results or different amount of results, and your test fails, it's not the problem. Let it be your task to adjust the code to make it work again;)

### To reuse the code from this project

Ensure you installed everything from the Prerequisites section and additinally install:

* [Git](https://git-scm.com/)

Open your unix terminal (or at least git bash on Windows) and execute the following commands(just copy&paste everything into the terminal and press Enter):

```bash
git clone git@github.com:autotesthow/selenidejs-demo.git selenidejs-demo \
&& cd $_ \
&& npm install \
&& code .
```

You'll see the project opened in the Visual Studio Code. Check the code in google-finds-selenide.js and run it by pressing Ctrl+Shift+\` on windows or Command+Shift+\` on Mac and execute the following command:

```bash
node google-finds-selenide.js
```

Enjoy!
