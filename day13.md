**# Day 13**

- [Section 9: Let's Build a Framework / Library!](#section-9-lets-build-a-framework--library)
  - [Project files:](#project-files)

# Section 9: Let's Build a Framework / Library!

The lectures were more of a code along and less of a theoretical knowledge.

Created a new library which would utilize the jQuery like methods to give greeting messages for Spanish and English languages.

The project majorly utilized the concepts of immediately invoked function expressions, function expressions, default object values, chain able methods, setting up prototype methods, aliasing functions and adding it to the global and so on..

Keeping meaningful comment on the code-base is always good idea.

## Project files:

`index.html`

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Document</title>
	</head>
	<body>
		<h1>Custom Greeting Library</h1>
		<script src="./jquery.js"></script>
		<script src="./greeter.js"></script>
		<script src="./app.js"></script>
	</body>
</html>
```

`greeter.js`

```jsx
// craete a execution context which allows to use reasonable things only

// passing global and jquery as a paramter
(function (global, $) {
	// utilize jquery like structure

	// use function constructor to create an object
	var Greeter = function (firstName, lastName, language) {
		return new Greeter.init(firstName, language, language);
	};

	var supportedLanguages = ["en", "es"];

	var greetings = {
		en: "Hello",
		es: "Hola",
	};

	var formalGreetings = {
		en: "Greetings",
		es: "Saludos",
	};

	var logMessages = {
		en: "Logged In",
		es: "Inicio sesion",
	};

	Greeter.prototype = {};

	// setting up the accessible methods when method called
	Greeter.prototype = {
		fullName: function () {
			return this.firstName + " " + this.lastName;
		},

		validate: function () {
			console.log(supportedLanguages.indexOf(this.language) === -1);
			if (supportedLanguages.indexOf(this.language === -1)) {
				throw "Language not supported";
			}
		},

		greeting: function () {
			return greetings[this.language] + " " + this.firstName + "!";
		},

		formalGreeting: function () {
			return formalGreetings[this.language] + " " + this.fullName();
		},

		greet: function (formal) {
			var message;

			if (formal) {
				message = this.formalGreeting();
			} else {
				message = this.greeting();
			}

			if (console) {
				console.log(message);
			}

			// 'this' refers to the calling object at execution time
			// makes method chainable
			return this;
		},

		log: function () {
			if (console) {
				console.log(logMessages[this.language] + ": " + this.fullName());
			}

			// making chainable
			return this;
		},

		setLanguage: function (language) {
			this.language = language;

			// make sure language is valid
			this.validate();

			// making chainable
			return this;
		},
	};

	// build an object and pass some default values if not provided
	Greeter.init = function (firstName, lastName, language) {
		var self = this;
		self.firstName = firstName || "";
		self.lastName = lastName || "";
		self.language = language || "";
	};

	// setting up prototypes to the Greeter object
	Greeter.init.prototype = Greeter.prototype;

	// setting up an alias for the function
	global.Greeter = global.G$ = Greeter;
})(window, jQuery);
```

`app.js`

```jsx
var greet = G$("Pank", "AJ", "es");

console.log(greet.greeting()); // Hola Pank!
console.log(greet.formalGreeting()); // Saludos Pank es
```
