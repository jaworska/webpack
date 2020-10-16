# webpack4
Sample configuration of Webpack 4

Rename Babel config file from `babelrc.js` to `.babelrc`

Jeśli interesujesz się Front-Endem od niedawna możesz się zapytać czym jest Webpack i po Ci on. Jest to bardzo przydatne narzędzie które wykonuje wiele zadań za Ciebie. Napisałem o tym trochę więcej przy okazji mojego wpisu o Webpack 1.

W tych czasach królują frameworki/biblioteki czyli Angular, React i Vue. Mają one swoje CLI które po zainstalowaniu nie wymaga większej konfiguracji. Jeśli jednak pracujesz w jakiejś innej technologii np. WordPress lub czysty JS to Webpack jest przydatny.

Co nowego?
W zasadzie to wypowiem się w stosunku do ostatniego mojego wpisu czyli wersji 1 🙂

Cała konfiguracja wydaje się jakby łatwiejsza? Webpack ma swoje CLI które już zawiera kilka opcji które wcześniej należało manualnie instalować.

Domyślnie pliki CSS/SASS są importowane do JS’a i na końcu tworzy się jeden bundle który zawiera wszystko. Można to jednak później rozdzielić na CSS i JS (ta konfiguracja to uwzględni).

Hehe tyle na pierwszy rzut oka 🙂 

Jak zacząć konfigurację?
Na początku zainstaluj (jeśli jeszcze go nie masz) globalnie Yarna. To program do obsługi pakietów Node’a. Jest odpowiednikiem npm jednak jest stabilny i nie wywala głupich błędów…

Następnie pobierz z mojego repozytorium na Githubie  konfigurację Webpacka. Umieść w odpowiednim folderze na Twoim komputerze.

https://github.com/bartcis/webpack4/tree/master

Będąc w folderze projektu w terminalu uruchom komendę `yarn install` by zainstalować wszystkie potrzebne pakiety.

Zanim uruchomisz Webpacka to przeczytaj ten wpis do końca bo wytłumaczę dalej co i jak.

Struktura plików
Jeśli Webpack to dla Ciebie nowość to wiedz:

I. Wszystkie pakiety są zdefiniowane w pliku package.json.

Na jego podstawie Yarn instaluje co trzeba. Tam też definiujesz komendy którymi będziesz uruchamiać Webpacka:

JavaScript4 lines
`"scripts": {
    "dev": "webpack --mode development --watch",
    "build": "webpack --mode production --watch"
},`

II. Webpack jest konfigurowany w pliku webpack.config.js

III. PostCSS wymaga oddzielnego pliku konfiguracyjnego postcss.config.js

IV. Babel wymaga z kolei pliku .babelrc

V. Zasoby z Twoim kodem JS i SASS są kompilowane do plików wykorzystywanych przez index.html


Pojedyncze uruchomienie

W trybie development czyli bez minifikacji i uglifikacji JS. To ułatwia debugowanie
`yarn dev`

Lub w trybie builda czyli wyjściowy plik JS jest nieczytelny i trudniej debugować
`yarn build`

Uruchomienie ciągłe

`yarn dev --watch`

`yarn build --watch`

postcss.config.js

PostCSS jest mega. Posiada masę narzędzi usprawniających pracę z CSS. Jeśli chcesz dodać jakiś konkretny moduł po prostu dodaj go do pliku konfiguracyjnego:

`module.exports = {
    plugins: [
        require('autoprefixer'),
        require('cssnano')
    ]
}`

A potem jeszcze zainstaluj odpowiedni pakiet np.
yarn add autoprefixer

https://bedekodzic.pl/webpack-4/