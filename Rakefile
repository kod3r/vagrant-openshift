#--
# Copyright 2013 Red Hat, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#++

require 'rubygems'
require 'bundler/setup'
require 'pry'
$stdout.sync = true
$stderr.sync = true

namespace :vagrant do

  desc "Install plugin into Vagrant"
  task :install do
    Rake::Task['build'].invoke
    name = Bundler::GemHelper.instance.send(:name)
    version = Bundler::GemHelper.instance.send(:version).to_s
    Bundler.with_clean_env do
      system("vagrant plugin install pkg/#{name}-#{version}.gem")
    end
  end
end

Bundler::GemHelper.install_tasks
task :default => "vagrant:install"
