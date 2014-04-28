angular-dialog-service
======================

!! Please use one of the release versions rather than the Master Branch.  The Master Branch has untested merges and changes and is a work in progress.  I urge you to always use a release version rather than linking directly to the Master Branch, as the Master Branch may change and may not always be backward compatible.

!! v4.x.x + is not backward compatible with versions 1,2,3,3.1  Please refer to the changes section to view what is different in v4.0

A complete AngularJS service with controllers and templates for generating application modals and dialogs for use with Angular-UI-Bootstrap and Twitter Bootstrap.  Supports, i18n, language translations for dialog headers, messages and buttons via angular-translate.

Demos 
- v1.0 : http://codepen.io/m-e-conroy/pen/ALsdF
- v2.0 : http://codepen.io/m-e-conroy/pen/AmBpL
- v4.0 : Coming Soon - for now refer to the example folder.

Release Versions:
- v1.0 : supports AngularJS 1.1.5 and below.
- v2.0 : supports AngularJS 1.2 +
- v3.0 : supports AngularJS 1.2 +, Angular UI Bootstrap 0.10.0
- v4.0 : supports AngularJS 1.2 +, Angular UI Bootstrap 0.10.0, Bootstrap 3 +

Predefined dialogs/modals for v4.0.0 and up:

1. dialogs.error(header,msg)
2. dialogs.wait(header,msg,progress)
3. dialogs.notify(header,msg)
4. dialogs.confirm(header,msg)
5. dialogs.create(url,ctrlr,data)

Predefined dialogs/modals for v3.1.0 and below:

1. $dialogs.error(header,msg,[static])
2. $dialogs.wait(header,msg,progess,[static])
3. $dialogs.notify(header,msg,[static])
4. $dialogs.confirm(header,msg,[static])
5. $dialogs.create(url,ctrlr,data,opts)

Dependencies:

v1.0

1.  Angular JS - www.angularjs.org (version 1.1.5 and less) 
2.  Angular UI Bootstrap - http://angular-ui.github.io/bootstrap/#/modal (version <= 0.6.0, Non-Bootstrap 3 Branch) with embedded templates.
3.  Twitter Bootstrap CSS (2+)

v2.0 Additional Dependencies

1.  Angular JS ngSanitize - http://code.angularjs.org/1.2.1/angular-sanitize.min.js
	- ngSanitize: http://docs.angularjs.org/api/ngSanitize (needed for ng-bind-html)

v3.0

1.  AngularJS 1.2 +
2.  Angular UI Bootstrap 0.10.0
3.  Twitter Bootstrap CSS 3.0.3
4.  AngularJS ngSanitize

v4.0

1. AngularJS 1.2 +
2. Angular UI Bootstrap Modal 0.10.0, with templates (http://angular-ui.github.io/bootstrap/#/modal)
3. Twitter Bootstrap CSS 3 + (includes 3.1.1)
4. Angular ngSanitize
5. Angular Translate (https://github.com/angular-translate)

CSS:

Included a css file that has a .modal class fix for Bootstrap and also has some predefined styles for the various modals described in the service.

v3.0 css file has the .modal class removed that had been a fix for a Bootstrap 3 display problem.  This has since been rectified by Angular UI and Bootstrap.

Changes:

v3.0

1.  Added support for Angular UI Bootstrap 0.10.0.
2.  Added the ability to customize the header on the error and wait dialogs.
3.  Added example files.

v4.0

1.  Removed '$' from the '$dialogs' service as this is reserved for core AngularJS naming.  The service is now just 'dialogs.'
2.  Changed 'dialogs' service from factory to provider, you can now use 'dialogsProvider' to set various options of the modals that were previously passed as parameters to the dialog's service methods.
	a. dialogsProvider.useBackdrop([true,false,'static']) - True or false to use a backdrop for the modal, 'static' to use a backdrop and disallow closing on mouse click of the backdrop.
	b. dialogsProvider.useEscClose([true,false]) - Whether or not to allow the use of the 'ESC' key to close the modal
	c. dialogsProvider.useClass([string]) - Sets an additional CSS class to the modal window
3.  Main module is no longer 'dialogs' as this would conflict with the new naming of the service.  It is now 'dialogs.main,' include that in your application's module definition to use this service.
4.  Added i18n support via Angular-Translate (https://github.com/angular-translate), use the '$translateProvider' to set language specific defaults.  Default language is currently 'en-US.'  An example is provided in the example folder that will show you how to change the defaults from English to Spanish.  Translations can be set on the following:
	a. DIALOGS_ERROR (modal header)
	b. DIALOGS_ERROR_MSG
	c. DIALOGS_CLOSE (modal button)
	d. DIALOGS_PLEASE_WAIT (modal header)
	e. DIALOGS_PLEASE_WAIT_ELIPS (modal header)
	f. DIALOGS_PLEASE_WAIT_MSG
	g. DIALOGS_PERCENT_COMPLETE (modal message partial)
	h. DIALOGS_NOTIFICATION (modal header)
	i. DIALOGS_NOTIFICATION_MSG
	j. DIALOGS_CONFIRMATION (modal header)
	k. DIALOGS_CONFIRMATION_MSG
	l. DIALOGS_OK (modal button)
	m. DIALOGS_YES (modal button)
	n. DIALOGS_NO (modal button)

Notes:

- Angular Translate: v4.0 requires angular-translate be included.
- Bootstrap 3: (v3.0 of this service no longer requires this fix) There's a problem with the actual modal being displayed even though it appears in the HTML code to be present.  I found that adding a "display: block" to Bootstrap 3's .modal class solved the problem.  
- It should not rely on including the Bootstrap JS.
- For version 2.0 + of this service module do not forget to include the ngSanitize Angular module.
