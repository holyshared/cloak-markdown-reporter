cloak-markdown-reporter
=======================

**cloak-markdown-reporter** is markdown reporter for [cloak](https://github.com/holyshared/cloak).  
Output in [markdown](http://daringfireball.net/projects/markdown/) format the report of code coverage.

[![Build Status](https://travis-ci.org/holyshared/cloak-markdown-reporter.svg?branch=master)](https://travis-ci.org/holyshared/cloak-markdown-reporter)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/holyshared/cloak-markdown-reporter/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/holyshared/cloak-markdown-reporter/?branch=master)
[![Coverage Status](https://coveralls.io/repos/holyshared/cloak-markdown-reporter/badge.png)](https://coveralls.io/r/holyshared/cloak-markdown-reporter)
[![Stories in Ready](https://badge.waffle.io/holyshared/cloak-markdown-reporter.png?label=ready&title=Ready)](https://waffle.io/holyshared/cloak-markdown-reporter)
[![Dependencies Status](https://depending.in/holyshared/cloak-markdown-reporter.png)](http://depending.in/holyshared/cloak-markdown-reporter)


Installation
------------------------------------------------

### Composer setting

Cloak can be installed using [Composer](https://getcomposer.org/).  
Please add a description to the **composer.json** in the configuration file.

	{
		"require-dev": {
			"cloak/cloak": "1.3.2.1"
			"cloak/markdown-reporter": "1.0.0"
		}
	}

### Install

Please execute **composer install** command.

	composer install


How to use
------------------------------------------------

### Setup for the report of code coverage

Setup is required to take a code coverage.  
Run the **configure** method to be set up.

	<?php

	$analyzer = Analyzer::factory(function(ConfigurationBuilder $builder) {

		$builder->reporter(new MarkdownReporter(__DIR__ . '/report.lcov'));

    	$builder->includeFile(function(File $file) {
        	return $file->matchPath('/src');
	    })->excludeFile(function(File $file) {
    	    return $file->matchPath('/spec') || $file->matchPath('/vendor');
	    });

	});


Example
------------------------------------------------

You can try with the following command.

	vendor/bin/phake example:basic
