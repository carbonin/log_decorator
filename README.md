# LogDecorator

Acts as a proxy to a configurable underlying logging mechanism,
permitting the code to be executed in absence of the logger.

Provides hooks to permit the "decoration" of log messages. By default,
the class and method name of the caller are added to the log message.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'log_decorator'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install log_decorator

## Usage

### Initilization
```ruby
logger = Logger.new # Instantiate an instance of the logger of your choice
logger.level = desired_log_level # Set up the logger as needed
LogDecorator.logger = logger # Tell LogDecorator to use the logger
```

### Use
Given:

```ruby
class MyClass
  include LogDecorator

  def self.method_1
    _log.debug "Called"
  end

  def method_2
    _log.debug "Called"
  end
end
```

Then:

```ruby
MyClass.method_1
```

Loggs:

```
MyClass.method_1 Called
```

and

```ruby
MyClass.new.method_2
```

Loggs:

```
MyClass#method_2 Called
```

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

