# TinyWeatherForecastGermany javadoc code docs

[![gitlab pages -> pipeline status](https://gitlab.com/tinyweatherforecastgermanygroup/twfg-javadoc/badges/main/pipeline.svg)](https://gitlab.com/tinyweatherforecastgermanygroup/twfg-javadoc/-/commits/main)

[-> see here for the **docs**](https://tinyweatherforecastgermanygroup.gitlab.io/twfg-javadoc/index.html)

[-> see here for the **overview** page](https://tinyweatherforecastgermanygroup.gitlab.io/index)

## Purpose -> *Why?*

**Target:** automatically generate **code documentation** for the Project [**Tiny Weather Forecast Germany**](https://codeberg.org/Starfish/TinyWeatherForecastGermany) by Pawel Dube ([@Starfish](https://codeberg.org/Starfish)).

***Note**: 'TWFG' is an inofficial abbreviation for **T**iny **W**eather **F**orecast **G**ermany.*

## Reason -> *What's the added value?*

* lower the bar for contributions from the public
* show case generation of UML diagrams for javadoc workflows

## Workflow -> *How does it work?*

**tl;dr** -> it runs completely **autonomously** once per day at 5:20am UTC on shared runners of **GitLab CI/CD**

The Gitlab CI/CD pipeline defined in [`.gitlab-ci.yml`](https://gitlab.com/tinyweatherforecastgermanygroup/twfg-javadoc/-/blob/c89a6b824fc2d59e0e669782251c7ca1728a8c5f/.gitlab-ci.yml) does the following:

1. update the shipped packages
2. install `graphviz` and `brotli`
3. clone the code repository from [codeberg.org](https://codeberg.org/Starfish/TinyWeatherForecastGermany) using git
4. run [`javadoc`](https://www.oracle.com/java/technologies/javase/javadoc.html) against the code repositories java files -> the [umldoclet](https://github.com/talsma-ict/umldoclet/) by [Talsma ICT](https://github.com/talsma-ict/) is used instead of the default doclet to produce **UML** diagrams during the process.
5. copy generated html assets to `public` directory

## Dependencies

* **OpenJDK 11** (contained in `openjdk:11-jdk` docker image)
* [umldoclet](https://github.com/talsma-ict/umldoclet/) -> **graphviz**
* **brotli** and **gzip** -> compression of assets (js, css, images)

## License/Copyright and Credits

GNU **G**ENERAL **P**UBLIC **L**ICENSE (**GPLv3**) please see the [`License`](https://gitlab.com/tinyweatherforecastgermanygroup/twfg-javadoc/-/blob/456a60ab2dff26ed74a76a963f32976eb7d99066/LICENSE) file for details.

**Copyright** of the *main* project -> **Tiny Weather Forecast Germany** --> Pawel Dube ([@Starfish](https://codeberg.org/Starfish))

This CI/CD script was created by Jean-Luc Tibaux (@eUgEntOptIc44).

The **[GZIP](https://en.wikipedia.org/wiki/Gzip) compression** feature (high priority for SEO) was integrated using intel shared by [Christian Danscheid](https://webd97.de/post/gitlab-pages-compression/).

The [umldoclet](https://github.com/talsma-ict/umldoclet/) by [Talsma ICT](https://github.com/talsma-ict/) uses [graphviz](https://gitlab.com/graphviz/graphviz) via [PlantUML](https://plantuml.com/).

### javadoc bugfixes

Bugfix to use javadoc with openjdk versions newer then 8 -> https://stackoverflow.com/questions/38621202/ignore-minor-errors-using-javadoc/63683772#63683772 -> `--ignore-source-errors` -> provided by user Marteng -> License: CC BY-SA 4.0

Bugfix to resolve javadoc search 'undefined' error -> https://stackoverflow.com/questions/52326318/maven-javadoc-search-redirects-to-undefined-url#52603413 -> `--no-module-directories` -> provided by user Radoslav Ivanov -> License: CC BY-SA 4.0

## Contributing

* As noted above contributions to **Tiny Weather Forecast Germany** are managed at the ['main'](https://codeberg.org/Starfish/TinyWeatherForecastGermany) code repository
* Please feel free to contribute to this script by opening issues and/or merge requests.
* [**Translations**](https://weblate.bubu1.eu/engage/tiny-weather-forecast-germany/) of Tiny Weather Forecast Germany are managed at the [**weblate** instance](https://weblate.bubu1.eu/projects/tiny-weather-forecast-germany/) provided by Marcus Hoffmann (@Bubu).
* For cybersec, privacy and/or copyright related issues regarding this repository please directly contact the maintainer **Jean-Luc Tibaux** (@eUgEntOptIc44)
