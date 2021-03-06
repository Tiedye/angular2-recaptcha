# Angular 2 : Typescript component for Google reCaptcha 2

This is just very simple Angular 2 component that implements Google [reCaptcha 2](https://www.google.com/recaptcha/intro/index.html).

Installation
--------------------------------------

Install it from npm:

```bash
npm install angular2-recaptcha
```

Usage
--------------------------------------

### SystemJS config

```js
System.config({
    map: {
        'angular2-recaptcha': 'node_modules/angular2-recaptcha'
    },
    packages: {
        app: {
            format: 'register',
            defaultExtension: 'js'
        },
        'angular2-recaptcha': {defaultExtension: 'js', main:'index'}
    }
});
```

### Module

```typescript
...
import { ReCaptchaModule } from 'angular2-recaptcha';
...
```

```typescript
 ...
@NgModule({
  imports: [...,ReCaptchaModule]
  })
  ...
```

### View

Use in template like below

```html
 <re-captcha site_key="<GOOGLE_RECAPTCHA_KEY>"></re-captcha>
```

Where **site_key** is the Google reCaptcha private key. Optionally you can also override the user interface language by setting e.g. `language="de"`.

## Callback

To catch the success callback, you will need to subscribe to `captchaResponse` event. The response token will be passed in the `$event` parameter.

```html
<re-captcha (captchaResponse)="handleCorrectCaptcha($event)" site_key="<GOOGLE_RECAPTCHA_KEY>"></re-captcha>
```

The event `captchaExpired` is triggered when the displayed image has expired. It does not have any event parameters.

You can request a new captcha to be displayed:
```typescript
ReCaptchaComponent::reset();
```
