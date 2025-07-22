# CodeIgniter 4 Phone Number Validation

![Packagist Version](https://img.shields.io/packagist/v/your-username/codeigniter4-phone-validation)
![License](https://img.shields.io/packagist/l/your-username/codeigniter4-phone-validation)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/your-username/codeigniter4-phone-validation/CI)

This Composer package provides a simple and efficient way for CodeIgniter 4 developers to validate phone numbers and add a phone number validation rule to their projects.

## Installation

You can install the package via Composer. Run the following command in your CodeIgniter 4 project:

```bash
composer require AaronMk44/codeigniter4-phone-validation
```

## Usage

Once the package is installed, you can start using the phone number validation rule in your controllers or models.

### Adding the Validation Rule

Open your form validation configuration file, typically found at `app/Config/Validation.php`. Add the custom validation rule as follows:

```php
public $ruleSets = [
    'phone_number' => 'required|is_phone_valid',
];
```

### Validating Phone Numbers

Now, you can use the `validate_phone_number` rule in your controller methods to validate phone numbers. Here's an example:

```php
public function register()
{
    $validation = \Config\Services::validation();
    $validation->setRules(
            [
                'phone' => 'is_phone_valid',
            ],
            [   // Errors
                'phone' => [
                    'is_phone_valid' => 'The phone is invalid',
                ]
            ]
        );
    if ($this->request->is('post') && $this->validation->withRequest($this->request)->run()) {
        // Valid phone number, proceed with registration
    } else {
        // Invalid phone number, handle errors
        $errors = $validation->getErrors();
        print_r($errors);
    }
}
```

That's it! You've successfully added phone number validation to your CodeIgniter 4 project.

## Support and Contributions

If you encounter any issues or have suggestions for improvements, please open an issue on the https://github.com/AaronMk44/ci4-phone-number-validation. Contributions are welcome! Fork the repository, make your changes, and submit a pull request.

## License

This package is open-source software licensed under the [MIT license](LICENSE).
