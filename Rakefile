namespace :greeting do 
  desc 'outputs hello to the terminal'
  task :hello do
    puts "hello from Rake!"
  end

  desc 'outputs hola to the terminal'
  task :hola do 
    puts 'hola de Rake!'
  end 
end

task :environment do
  require_relative './config/environment'
end 

namespace :db do 
  desc 'migrate changes to your database'
  # this is creating a task dependency. this line tells Rake to run the environment task before it can run migrate. 
  # this is bcos the student class' create_table method requires access to the `config/environment.rb` file bcos that's
  # where the DB constant is defined and student class is loaded.
  task migrate: :environment do 
    Student.create_table
  end 

  desc 'seed the database with some dummy data'
  task seed: :environment do
    require_relative './db/seeds.rb'
  end 

  desc 'check if migration and populating db was successful'
  task check: :environment do
    puts "Student.all: #{Student.all}"
  end 

end 


desc 'drop into the Pry console'
task :console, :environment do
  Pry.start
end