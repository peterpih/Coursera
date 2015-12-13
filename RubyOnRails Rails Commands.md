#Rails Commands

<pre>
<b>rails g</b>enerate <b>model</b> <em>model_name (singular)</em>
<b>rails g</b>enerate <b>controller</b> <em>controller_name (plural)</em>

<b>rails generate migration</b> <em>migration_name</em>

<b>rails s</b>erver

<b>rails new</b> <em>app_name</em>
</pre>

###Generating a Model

<pre>
<b>rails generate model<b> <em>lesson order:integer lesson:text text:text</em>
</pre>
generates :
'''
	app/models/sentence.rb
	db/migrate/20151213121015_create_sentences.rb
	test/fixtures/sentences.yml
	test/models/sentence_test.rb
	
