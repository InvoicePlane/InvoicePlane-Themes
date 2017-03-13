# Development Information for InvoicePlane v1 Themes

You want to develop a new theme for InvoicePlane? Awesome! This guide will help you to quickly create your own theme and publish it in the InvoicePlane Theme repository. 

### Theme concept introduction

Themes do not override the standard theme but replace it. Themes use Sass as the main language and rely on some requirements like Bootstrap.

#### Theme structure

All themes use the same structure. First, the variables are imported. The are used by Bootstrap, the core styles and third-party plugins like Select2.

    @import "ip_variables";
    @import "variables";

After that all dependencies are imported. Bootstrap is imported by the core to make sure only needed components are loaded.

    @import "../../core/scss/bootstrap";
    @import "../../../node_modules/font-awesome/scss/font-awesome";
    @import "includes/select2";
    @import "../../../node_modules/dropzone/src/dropzone";
    @import "../../core/scss/bootstrap-datepicker";

Last but no least the InvoicePlane core styles are loaded.

    @import "../../core/scss/core";

#### Warning!
Do **not** change this structure and the imports, as missing styles may break the application completely! If you want to add any styles or override existing styles, add them **below the core import**. We will not support any broken themes that remove, replace or change any core files.

If you think a specific part should be changed, join the chat or create a new topic in the community forums.

===

### Development requirements

To build your own theme you need to fulfill the following requirements:

* Have Node.js and npm installed on your machine  
    We do recommend using the latest stable version of Node.js and npm.
* Have `grunt-cli` installed globally for npm

### Theme File structure

A theme consists of many different files. All files are explained in this chapter so you know what you have to modify and how.

    theme_indentifier/
    ├── css
    │   └── ...
    ├── sass
    │   ├── _ip_variables.scss
    │   ├── _variables.scss
    │   ├── monospace.scss
    │   ├── reports.scss
    │   ├── styles.scss
    │   ├── templates.scss
    │   └── welcome.scss
    └── theme_indentifier.theme

#### theme_indentifier.theme
The `theme_indentifier.theme` file is the main file of your theme and absolutely needed for your theme to be accepted in the theme repository and to be selectable in the InvoicePlane settings. The file consists of various information about the theme:

| Setting           | Description                                               | Example Value                         |
| ----------------- | --------------------------------------------------------- | ------------------------------------- | 
| TITLE             | The title that will show up in the InvoicePlane settings  | `InvoicePlane Blue`                   |
| DESCRIPTION       | Short description about the theme                         | `A more colorful InvoicePlane theme.` |
| VERSION           | The version of your theme, should use semver              | `InvoicePlane Blue`                   |
| AUTHOR            | Your name, pseudonym or company name                      | `InvoicePlane Developers`             |
| AUTHOR_WEBSITE    | Your website, must start with http:// or https://         | `https://invoiceplane.com/`           |
| LICENSE           | The license for the theme                                 | `MIT`                                 |
| REQUIRES          | Minimum version of InvoicePlane required for this theme   | `InvoicePlane Blue`                   |
| TESTED_WITH       | Highest version of InvoicePlane the theme was tested with | `1.5.0`                               |

The following information **must** be provided:

* TITLE
* AUTHOR
* LICENSE
* REQUIRES
* TESTED_WITH

Please notice that you have to surround all information with single quotes.

#### _ip_variables.scss
This file contains variables specificly added for InvoicePlane. You may change the values for variables in this file but do not remove or rename any variables.

#### _variables.scss
This file contains variables needed for Bootstrap and some core styles. You may change the values for variables in this file but do not remove or rename any variables.

#### monospace.scss
This file contains the styling for monospaced amounts. You may change the styling and the font that should be used for amounts.

#### reports.scss
Contains the styles that are used for reports.

#### styles.scss
Contains the styles for the InvoicePlane application. As mentioned above: only add new styles but do not alter or delete existing parts of this file. These styles are also used for public quotes or invoices.

#### templates.scss
Contains the styles that are used for PDF templates.

#### welcome.scss
A smaller version of styles.scss that is used for the welcome screen and the setup.

#### `css` directory

The `css` directory contains the compiled stylesheets. You don't and shoudln't change any files in this directory manually.

===

### Guidelines for developing a theme

Before you start to work on your theme please read these guidelines as violating them may lead to a rejection for the theme repository.

* The theme identifier must not contain the string `invoiceplane` in any way. Only official themes like `invoiceplane_default` are allowed to use the string in its identifier. However, using `ip` is okay.
* Choose your identifier wisely. It should not be a very generic string like `material` or `metro`. Add you name, pseudonym or company name to the string like this: `john_doe_material`, `` or ``
* Make sure you provide detailed information about the theme and yourself in the .theme file.
* Do not use any vendor prefixes like `-moz-border-radius` as they are automatically added in the compilation process.
* Please add at least one screenshot of your theme with the name `screenshot.jpg` or `screenshot.png`. to the theme root folder. The screenshot should show the dashboard. Feel free to add additional screenshots but pleas name them `screenshot_2.jpg`, `screenshot_3.jpg` and so on.

===

### Developing a new theme

The development of a theme is done directly within the InvoicePlane application. Please clone the repository to your machine or download the package from our website. After that, run the command `npm install` in the root directory of the InvoicePlane app. This will install all needed components to build the theme.

You may copy an existing theme (except the `core` folder) and modify it to match your needs. Starting from scratch is not recommended.

#### Using Grunt

Grunt, the task runner used for the theme compilation. There are two tasks available:

* `grunt dev`
    This command is used to develop a theme. It will automatically run an initial compilation and then start watching the theme files. If oyu change a theme file Grunt will automatically recompile the theme so you can continue working without interruptions. To cancel the watch process, use `ctrl` + `c`. The development command will not compress any CSS files to make debugging easier. Source maps are generated too.
* `grunt build`
    The grunt build command is needed to prepare your theme styles for release. The command will compile all styles and compress them to save space. It will also delete any source maps as they are usually not needed in production environments.

#### Publishing your theme

We do recommend to add your theme to this theme repository. It will be and remain the main storage point for themes and may be integrated into the InvoicePlane website. To add your theme, read the corresponding section in the [main readme](/README.md).

After adding your theme to the repository, you may also promote it in the InvoicePlane community forums. We have a dedicated section for theme and template sharing.

===

### Questions or need help?

[![Community Forums](https://img.shields.io/badge/Help%3A-Community%20Forums-429ae1.svg)](https://community.invoiceplane.com/)  
[![Issue Tracker](https://img.shields.io/badge/Development%3A-Issue%20Tracker-429ae1.svg)](https://development.invoiceplane.com/)  
[![Slack Chat](https://img.shields.io/badge/Development%3A-Slack%20Chat-429ae1.svg)](https://invoiceplane-slack.herokuapp.com/)  
