# Lumen Form Request

This is a small library to port [form request](https://laravel.com/docs/5.8/validation#form-request-validation)'s from Laravel 5.8 to Lumen 5.8.

To use this library register the service provider in `bootstrap/app.php`:

	/*
	|--------------------------------------------------------------------------
	| Register Service Providers
	|--------------------------------------------------------------------------
	|
	| Here we will register all of the application's service providers which
	| are used to bind services into the container. Service providers are
	| totally optional, so you are not required to uncomment this line.
	|
	*/

	$app->register(Monsterlane\Providers\FormRequestServiceProvider::class);

Create files in `App\Http\Requests` using the following format:

	<?php

	namespace App\Http\Requests;

	use Monsterlane\Http\FormRequest;

	class SaveRequest extends FormRequest
	{
	    /**
    	 * Verify we are authorized to call the route.
	     *
	     * @return bool
	     */
	    public function authorize(): bool
	    {
	        return true;
	    }

	    /**
	     * Get the validation rules that apply to the request.
	     *
	     * @return array
	     */
	    public function rules(): array
	    {
	        return [];
	    }
	}

Use them in a controller:

    public function myRoute(SaveRequest $request, ...): JsonResponse

---

MIT License

Copyright (c) 2022 Jonathan Down

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
