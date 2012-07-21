## Mocha issue 92

This is a Rails project which attempts to reproduce the issue seen in [Mocha issue 92](https://github.com/freerange/mocha/issues/92)..

### What I did

I basically followed the [minitest-rails instructions](https://github.com/blowmage/minitest-rails/) as follows :-

```
$ rails new mocha-issue-92 --skip-test-unit
```

```ruby
# Gemfile
group :test, :development do
  gem 'minitest', '3.2.0'
  gem 'minitest-rails'
  gem 'mocha', require: false
end
```

```
$ bundle install
$ rails generate mini_test:install
```

```ruby
# test/minitest_helper.rb (at bottom of file)
require "mocha"
```

```
$ rails generate model User
```

```ruby
# test/models/user_test.rb (uncommented following lines)
test "the truth" do
  assert true
end
```

```
$ rake db:create:all
$ rake db:migrate
$ rake minitest

Run options: --seed 27614

# Running tests:

.

Finished tests in 0.095963s, 10.4207 tests/s, 10.4207 assertions/s.

1 tests, 1 assertions, 0 failures, 0 errors, 0 skips

```
