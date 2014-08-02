# Publish pretty [rspec](http://rspec.info/) reports

This is a ruby Rspec custom formatter which generates pretty html reports showing the results of rspec tests. This gem was build to use Rspec 2.8.0. If you want to use it with newer
versions of Rspec then you need to include the rspec legacy formatters - see below for instructions.

## Install

```
  gem install rspec_reports_formatter
```

ideally just add it to your bundler Gemfile as follows:

```ruby
 gem 'rspec_reports_formatter'
```

## Use
When running your rspec tests with rspec 2.8.0 just use the custom formatter:

This should work:

```
 rspec -f RspecHtmlFormatter spec
```

If not you can explicitly add in a require as follows:

```
 rspec --require rspec_html_formatter.rb --format RspecHtmlFormatter spec
```

If you are using a more recent version of Rspec (3.0.0 onwards) then you must include the legacy formatter gem into your project by adding it to your Gemfile:

```ruby

# Your gemfile
group :development do
  gem 'rspec','~> 3.0.0.rc1'
  gem 'bundler', '~> 1.0'
  gem 'rspec-legacy_formatters'
  gem 'rspec_html_formatter'
end

```

Then use it at the command line:

```
 rspec --require rspec/legacy_formatters -f RspecHtmlFormatter spec
```
It will probably throw out some deprecation warnings. Sorry. I will probably make a version of this reporting specifically for rspec 3.0.0 and onwards at some point.


![example overview report]
(https://raw.githubusercontent.com/kingsleyh/rspec_reports_formatter/master/.README/rspec_reports_overview.png)

![example report]
(https://raw.githubusercontent.com/kingsleyh/rspec_reports_formatter/master/.README/rspec_reports_report.png)

If you want to provide some generated documentation for the tests you can put comments in the rspec tests like this:

```ruby
  #-> Given I have ordered a vegetarian pizza
  #-> When I eat the pizza
  #-> Then my tummy is full

```

The #-> notation is picked up and passed through a Gherkin syntax highlighter. So it was designed to use with Given,When,Then. But in theory you can put other text there too.