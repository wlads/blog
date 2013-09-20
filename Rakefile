require "rubygems"
require "bundler/setup"
require "stringex"

posts_dir    = "_posts"
new_post_ext = "md"

# Task Borrowed from Octopress
# usage rake new_post[my-new-post] or rake new_post['my new post'] or rake new_post (defaults to "new-post")
desc "Begin a new post in #{posts_dir}"
task :new_post, :title do |t, args|
  raise "### You haven't set anything up yet." unless File.directory?(posts_dir)
  mkdir_p "#{posts_dir}"
  args.with_defaults(:title => 'new-post')
  title = args.title
  filename = "#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "date_pt_BR: #{Time.now.strftime('%d %b %Y')}"
    post.puts "categories: "
    post.puts "---"
  end
end

# Task Borrowed from Octopress
# usage rake preview
desc "preview the site in a web browser"
task :preview do
  puts "Starting to watch source with Jekyll and Compass."
  jekyllPid = Process.spawn("jekyll serve watch")
  compassPid = Process.spawn("compass watch")

  trap("INT") {
    [jekyllPid, compassPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
    exit 0
  }

  [jekyllPid, compassPid].each { |pid| Process.wait(pid) }
end
