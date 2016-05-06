
# Dependencies ==============================
require 'json'

# Configuration =============================

# Set the default task to package up the extension
task :default => :package

# Helpers ===================================

def package

  # Read in the manifest file
  manifest_file = File.read('Manifest.json')
  manifest = JSON.parse(manifest_file)

  output_dir = ".."

  # Set the filename of the archive
  archive_file = "%s/%s-%s.zip" % [output_dir, File.basename(Dir.pwd), manifest["version"]]

  # Build up the command to be used to create the zip file
  cmd = "zip -9 -r %s ../%s -x '*.git*' -x '*test*/' -x '*images/*' -x '*.md' -x '*Rakefile'" % [archive_file, File.basename(Dir.pwd)]

  puts "Creating package: %s" % [archive_file]
  `#{cmd}`
end

# Tasks =====================================

# rake package
# Package up the files into a zip file
desc "Package up the extension as a zip file, naming it after the manifest version"
task :package do
  package
end
