## Translations

The Spiral i18n component, based on the symfony/translator package, provides interfaces for internationalization. This component is included in the web bundle by default. It allows you to translate your application into multiple languages, which is crucial for applications that aim to serve users from different regions and language backgrounds.

The i18n component automatically loads all locale files located in `app/locale/{lang}` directories. You can get a list of available locales and change the locale using the `setLocale` method. The framework supplies a default configuration automatically, but you can alter the configuration by creating the `app/config/translator.php` file.

### Links and materials to read more:
1. [Translations in Spiral Framework](https://spiral.dev/docs/advanced-i18n/current/en)
