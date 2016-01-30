###Generating a Model

<pre>
<b>rails generate model<b> <em>lesson order:integer lesson:text text:text</em>
</pre>
generates the following files :
```
app/models/sentence.rb
db/migrate/20151213121015_create_sentences.rb
test/fixtures/sentences.yml
test/models/sentence_test.rb
```
###app/models/sentence.rb
```
class Sentence < ActiveRecord::Base
end
```
###db/migrate/20151213121015_create_sentences.rb
```
class CreateSentences < ActiveRecord::Migration
  def change
    create_table :sentences do |t|
      t.integer :order
      t.text :lesson
      t.text :text

      t.timestamps null: false
    end
  end
end
```
###test/fixtures/sentences.yml
```
# Read about fixtures at http://api.rubyonrails.org/classes/ActiveRecord/FixtureSet.html

one:
  order: 1
  lesson: MyText
  text: MyText

two:
  order: 1
  lesson: MyText
  text: MyText
```
###test/models/sentence_test.rb
```
require 'test_helper'

class SentenceTest < ActiveSupport::TestCase
  # test "the truth" do
  #   assert true
  # end
end
```
