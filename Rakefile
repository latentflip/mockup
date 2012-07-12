require 'erb'

task :default => [:build ]

def write_output( filename, result )
  filename = filename.split( '/' ).last
  filename = filename.ext('html')
  File.open( filename, 'w+' ) do |f|
    f.write( result )
  end
end

def partial( name )
  filename = "source/partials/#{name}"

  if File.exists? filename
    File.open( filename, 'r' ).read.chomp
  end
end

task :build do
  sources = FileList["source/*.erb"]

  sources.each do |f|
    page = ERB.new( File.open( f, 'r' ).read )
    write_output f, page.result
  end
end
