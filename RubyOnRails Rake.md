for **psql** commands look [here](https://github.com/peterpih/Miscellaneous/blob/master/PSQL%20and%20Postgres.md)

###Rake commands
<pre>
<b>rake db:migrate:redo VERSION=</b><em>20080906120000</em>  <em>(does <b>down</b> then <b>up</b>)</em>
<b>rake db:migrate:up VERSION=</b><em>20080906120000</em>
<b>rake db:migrate:down VERSION=</b><em>20080906120000</em>
</pre>

[Run a single migration](http://stackoverflow.com/questions/753919/run-a-single-migration-file)

###Check the tables
<pre>
<b>\c</b> <em>database name</em>   <em>(to **connect** to a database)</em>
<b>\d</b>                 <em>(to see the **tables** in the database)</em>

###Rake Migration file  
**db/migration/**20160129073118_create_recc_book_categories.rb
<pre>
class CreateReccBookCategories < ActiveRecord::Migration
  def change
    create_table :recc_book_categories do |t|
      t.text :name
      t.integer :reccbookcat_id

      t.timestamps null: false
    end
  end
end
</pre>

