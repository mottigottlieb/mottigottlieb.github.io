---
layout: post
title:  "Rails Generator Flags"
date:   2016-12-18 21:58:59 -0500
---


When developing Rails applications using generators I personally prefer generating one segment at a time. However, a generator by default may come with additional files.
Thankfully, rails provide flag helpers that can be used to skip additional files. 

###Model Generator Flags

Running `rails generate model Name` will create a model,  migration, along with 2 tests files.

	  	 db/migrate/20161219020255_create_table.rb
	  	 app/models/model.rb
		   test/models/model_test.rb
		   test/fixtures/model.rb
									 
You can use the following flags:

`	--no-test-framework`         
	`--skip-migration`
	
###Controller Generator Flags

Running `rails generate controller Name` will create views and assets folders, along with helper and test files.

           app/controllers/name_controller.rb
           app/views/name
           test/controllers/name_controller_test.rb
           app/helpers/name_helper.rb
           app/assets/javascripts/name.coffee
           app/assets/styleesheets/name.scss

You can use the following flags:

    --no-test-framework
    --skip-helper
    --skip-template-engine

 

	



