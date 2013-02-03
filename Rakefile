require "bundler/gem_tasks"
require 'rspec/core/rake_task'
require 'cucumber'
require 'cucumber/rake/task'

namespace :test do
  RSpec::Core::RakeTask.new(:rspec) do |t|
    t.rspec_opts = "--color"
  end

  Cucumber::Rake::Task.new(:features) do |t|
    t.cucumber_opts = "features --format pretty --tags ~@wip"
  end

  namespace :features do
    Cucumber::Rake::Task.new(:wip) do |t|
      t.cucumber_opts = "features --format pretty --tags @wip --wip"
    end

    Cucumber::Rake::Task.new(:travis) do |t|
      t.cucumber_opts = "features --format pretty --tags @travis"
    end
  end
end

desc "Run all tests"
task :test => ['test:rspec', 'test:features']

desc "Create a test project"
task :run do
  sh "bin/calatrava create test --dev"
end

namespace :gem do
  Bundler::GemHelper.install_tasks
end
