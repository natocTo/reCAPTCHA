# reCAPTCHA 2.x

## Installation

This version is suitable for Nette 2.4.

```sh
$ composer require minetro/recaptcha:~2.1.1
```

## Configuration

```yaml
extensions:
    recaptcha: Minetro\ReCaptcha\DI\ReCaptchaExtension

recaptcha:
    secretKey: ***
    siteKey: ***
```

## Usage

```php
use Nette\Application\UI\Form;

protected function createComponentForm() 
{
    $form = new Form();
    
    $form->addReCaptcha('recaptcha', $label = 'Captcha')
        ->setMessage('Are you bot?');
    
    $form->addReCaptcha('recaptcha', $label = 'Captcha', $required = FALSE)
        ->setMessage('Are you bot?');
    
    $form->addReCaptcha('recaptcha', $label = 'Captcha', $required = TRUE, $message = 'Are you bot?');
    
    $form->onSuccess[] = function($form) {
        dump($form->getValues());
    }
}
```

## Rendering

```smarty
<form n:name="myForm">
	<div class="form-group">
		<div n:name="recaptcha"></div>
	</div>
</form>
```

Be sure you place this script before `</body>` element.

```html
<!-- re-Captcha -->
<script src='https://www.google.com/recaptcha/api.js'></script>
```
