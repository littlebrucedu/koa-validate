koa-validate
============

[![Build Status](https://travis-ci.org/RocksonZeta/koa-validate.svg?branch=master)](https://travis-ci.org/RocksonZeta/koa-validate)
[![Coverage Status](https://coveralls.io/repos/RocksonZeta/koa-validate/badge.png)](https://coveralls.io/r/RocksonZeta/koa-validate)
[![Coverage Status](https://coveralls.io/repos/RocksonZeta/koa-validate/badge.png?branch=master)](https://coveralls.io/r/RocksonZeta/koa-validate?branch=master)
[![NPM version](https://badge.fury.io/js/koa-validate.svg)](http://badge.fury.io/js/koa-validate)
![dependencies](https://david-dm.org/RocksonZeta/koa-validate.png)

validate koa request params and format request params 

##installation
```
$ npm install koa-validate
```

## basic usage:
```javascript
	app.use(require('koa-body')());
	app.use(require('koa-validate')());
	app.use(require('koa-router')(app));
	app.post('/signup',function*(){
		this.checkBody('name').optional().len(3,20);
		this.checkBody('email').isEmail();
		this.checkBody('password').notEmpty().len(3,20);
		this.checkBody('nick').optional().empty().len(3,20);
		this.checkBody('age').toInt();
		if(this.errors){
			return this.body = this.errors;
		}
		this.body= 'ok';
	});
```