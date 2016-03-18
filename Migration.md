[**Migration** (RailsGuide.org)](http://guides.rubyonrails.org/v3.2/migrations.html)

[Migration for change column (SO)](http://stackoverflow.com/questions/2799774/rails-migration-for-change-column)

To create a Migration
<pre>
<b>rails generate migration</b> <em>name-of-migration</em>  
<em>Rails will create a new migration file in db/migration</em>

<b>rename_table</b>  <em>:old-table,  :new-table</em>   <em>( note _id_seq will automatically be renamed )</em>
<b>rename_column</b> <em>:table-name,  :old-column,  :new-column</em>

<pre>
