namespace :tags do
  task :generate do
    puts 'Generating tags...'

    include Jekyll::Filters

    options = Jekyll.configuration({})
    site = Jekyll::Site.new(options)
    site.read_posts('')

    html =<<-HTML
---
layout: default
title: Tags
---

<h2>Tags</h2>

    HTML

    site.categories.sort.each do |category, posts|
      html << <<-HTML
      <h3 id="#{category}">#{category}</h3>
      HTML

      html << '<ul class="posts">'
      posts.each do |post|
        post_data = post.to_liquid
        html << <<-HTML
          <li>
            <div>#{date_to_string post.date}</div>
            <a href="#{post.url}">#{post_data['title']}</a>
          </li>
        HTML
      end
      html << '</ul>'
    end

    File.open('tags.html', 'w+') do |file|
      file.puts html
    end

    puts 'Done.'
  end
end