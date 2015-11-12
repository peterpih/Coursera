***Videos:***   
https://www.youtube.com/watch?v=Im1lyxSZEu4

###Logging output
```
logger.debug <blah>          # => log/developement.log
Rails.logger.debug <blah>    # => log/test.log
```

https://robots.thoughtbot.com/how-we-test-rails-applications  
**book chapter**: http://www.justinweiss.com/files/practicing-rails-sample.pdf  

From: http://jakegoulding.com/presentations/rspec-structure/#slide-0  
**describe** and **context** group related tests together, they are the same method  
Rspec encourages to organize by *things*, tests usually involved changes in *state*  

Use **context** for *states*, but not available at the top level  

```
context "when the student is sick"
```
Use **describe** for *things*  
```
describe "#matriculate"
```
**context** names should not be the same as method names, they explain why the user calls the method
```
# Bad:
describe #assign

# Good:
context "assingning homework to students"
```
###before vs let
**before** runs code, use for *actions*  
**let** lazily runs code, when first called, use for *dependencies*, assigning values  

For *actions*:
```
# Bad:
let(:dummy) do
  @classroom.initialize_roster
end

# Good:
before do
  @classroom.initialize_roster
end
```
For *depedencies*:
```
# Bad:
before { @grade_levels = [1, 2, 3] }

# Good:
let(:grade_lavels) { [1, 2, 3] }
```
**context** is used for *state*, **before** is used to get to that *state*  

###let vs subject
Use **subject** for things you are testing, use **let** for *dependencies*  
###before vs let
```
# Bad:
let(:classroom) { Classroom.new(grade: 5) }

# Good: (also names subject)
subject(:classroom) { Classroom.new(grade: 5) }
```
Note: If your constructor takes no parameters, there's no need to define subject, but giving it a name is still a good idea.  

###subject & describe
**describe** is used for *things*, **subject** specifies thet things to test  
```
# At top level:
describe ParentNotifier do
  subject(:notifier) do
    ParentNotifier.new(phone: '1.555.555.5555')
  end
end

# At nested level:
describe ParentNotifier do
  subject(:notifier) do
    ParentNotifier.new(phone: '1.555.555.5555')
  end

  describe "the result of calling the parent" do
    subject(:call_result) { notifier.call }
  end
end
```
**Remove weak words**
- Don't use "should" in your test names.
  ```
  # Bad:
  it "should add the student to the class"
  
  # Good:
  it "adds the student to the class"
  ```
- Instead, say what will happen.
- Running the test will tell you if it is true or not.
- Corollary: prefer active verbs.

**One assertion per test**  

- Shows exactly what functionality is broken.
- One *logical* assertion.
  ```
  # Bad:
  it "..." do
    homework.should be_available
    homework.should_not be_expired
  end
  
  # Good:
  it "..." { homework.should be_available }
  it "..." { homework.should_not be_expired }
  ```
- Create custom matchers if you need multiple steps.
- Don't be afraid of throwing exceptions.

###A Typcical Test
```
describe Classroom do
  context "#a_mess?" do
    it "should return true after a party" do
      classroom = Classroom.new
      classroom.throw_pizza_party
      classroom.a_mess?.should be_true
    end
  end
end

# Output:
Classroom
  #a_mess?
    should return true after a party
```

###A Better Test
```
describe Classroom do
  subject(:classroom) { Classroom.new }
  context "when the children are rowdy" do
    before { classroom.throw_pizza_party }
    it { should be_a_mess }
  end
end

# Output:
Classroom
  when the children are rowdy
    should be a mess
```
