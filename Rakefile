require 'rubygems'
require 'rubygems/package_task'
require 'rubygems/specification'
require 'date'

Dir[File.join(
  File.expand_path(File.dirname(__FILE__)),
  'tasks/**/*.rake'
)].each { |rake| load rake }

#### MISC TASKS ####

desc "list tasks"
task :default do
  puts `rake -T`.split("\n").select { |line| /^[^(].*$/ }
end

desc "Outstanding TODO's"  
task :todo do  
  files = ["**/*.{rb,rake}" "bin/*", "README.mkdn"]
  
  File.open('TODO','w') do |f|
      FileList[*files].egrep(/TODO|FIXME/) do |file, line, text|
      output = "#{file}:#{line} - #{text.chomp.gsub(/^\s+|\s+$/ , "")}"
    
      puts output
      f.puts output
    end
  end
end