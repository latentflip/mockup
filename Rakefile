require 'erb'

task :default => [:build ]

def write_output( filename, result )
  filename = filename.split( '/' ).last
  filename = filename.ext('html')
  File.open( filename, 'wb' ).write( result )
end

def partial( name )
  filename = "source/partials/#{name}.partial"

  if File.exists? filename
    File.open( filename, 'rb' ).read.chomp
  end
end

task :build do
  sources = FileList["source/*.erb"]

  sources.each do |f|
    page = ERB.new( File.open( f, 'rb' ).read )
    write_output f, page.result
  end
end
