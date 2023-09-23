# Fork of Add-on Contact Form 7 – MailPoet 3 - with Accessibility fixes

This is a fork of the [Add-on Contact Form 7 – MailPoet 3](https://fr.wordpress.org/plugins/add-on-contact-form-7-mailpoet/) WordPress plugin.

It was made in order to fix some accessibility issues and to work with the [Contact Form 7 fork that aims to fix accessibility issues](https://github.com/juliemoynat/contact-form-7/releases) too.

## What have been fixed

Accessibility issues, Contact Form 7 compatibility and JavaScript compatibility have been improved.

### 1. Compatibility of lists checkboxes with Contact Form 7

The latest versions of Contact Form 7 have changed important things to make error messages work:

- On each field: 
    - Add `aria-required` attribute (with value `true` or `false` according to the admin configuration);
    - Add `aria-invalid` attribute (with value `true` or `false` according to the status).
- Previously, there was a class on the container around a field or around a group of fields. Now, it is a `data-name` attribute.

### 2. Accessibility of lists checkboxes

#### Group of checkboxes

- Transform the first `span` container into a `div`;
- Transform the second `span` container into a `fieldset`;
- Transform the first `label` into a `legend`;
- Create a unique ID for each field;
- Add `for` attribute for the `label`;
- Remove `br` at the end of the `span`.

#### One checkbox alone

- Add `for` attribute for the `label`;
- Remove `br` at the end of the `span`;
- Close the hidden `input` tag.

### 3. Unsubscribe checkbox

- Add `for` attribute for the `label`;
- Remove `br` at the end of the `span`;
- Remove space between field and label.

### 4. JavaScript compatibility (jQuery to Vanilla)

When scripts are minified, an error occurred with the jQuery code (“jQuery is undefined”). So it was required to transform it into Vanilla code in order to make it possible for users to subscribe to the lists they want.

### 5. Bug: people were subscribing to lists even if no checkbox is checked

Add a condition so that values in the hidden field (`input[name="fieldVal"]`) are added only if checkboxes are checked by default.

---

## How to contribute?

This fork must stay close to the evolving changes of the original plugin and so it must stay up to date.

This repository is a fork from the original plugin. The work is in progress on the `a11y-fixes` branch in order to be make updates from the original plugin easier.

### Using specific comment tags

To make it easier to merge changes with new updates, changes in the code is documented. Make sure to wrap the section of code you’ve changed with the following comment tags:

```php
/**
 * #cf7-a11y-start
 * Describe quickly in English the changes made
 */

// code

/** #cf7-a11y-end */
```

### Commenting original code

If you ever want to remove a whole chunk of code (ie. if statement, a whole function, etc.), comment the original code and in the `#cf7-a11y-start` comment tag, quickly explain *why* this has been removed, especially if it has to do with web accessibility.

For example, this could look like this (this example is not taken from the original plugin by the way):

```javascript
/**
 * #cf7-a11y-start
 * Remove role="button" : if button is needed
 * use <button> tags instead of <a> tags.
 */

// if (link) {
//    link.setAttribute('role', 'button')
// }

/** #cf7-a11y-end */
```

## How to use this plugin fork into your WordPress website

1. Download [the last release of this fork](https://github.com/juliemoynat/fork-add-on-contact-form-7-mailpoet/releases);
1. Into your `wp-content/plugins/` folder, create a new folder named `add-on-contact-form-7-mailpoet-a11y`;
1. Extract the ZIP file of the release into this new folder (without the parent folder);
1. Get your language for this plugin fork:
	1. Go on [the official “Translating WordPress” page for Add-on Contact Form 7 – MailPoet 3](https://translate.wordpress.org/projects/wp-plugins/add-on-contact-form-7-mailpoet/language-packs/) and download the translation files that you want (no French translation at the moment);
	1. Extract the files into your `wp-content/languages/plugins` folder.

### Important note: No automatic updates

1. This forked plugin is only available on GitHub so it will not benefit from automatic updates on your WordPress website.
1. The translations will not benefit from automatic updates on your WordPress website either.

**You will need to update the forked plugin and translations manually by repeating the steps detailed above.**

If you have a GitHub account, you can **watch the GitHub repository** to be notified when a new release is available:

1. Click on the “Watch” button on the top of [the repository page](https://github.com/juliemoynat/fork-add-on-contact-form-7-mailpoet/);
1. Then click on “Custom”;
1. Check the “Releases” checkbox;
1. Click on the “Apply” button;
1. You will receive an email when a release is available.
