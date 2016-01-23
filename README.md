# RScratch

By Avishek Jana

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'rscratch'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install rscratch

After you install RScratch, you need to run the generator:

    $ rake rscratch:install:migrations

The generator will create few migration files, will contain gem data. It is imperative that you take a look at it. When you are done, you are ready to run migration using the following command:

    $ rake db:migrate

You should restart your application after installing RScratch gem.

## Usage
Add this following line in rescue block of your your code. An example is given below

```ruby
  Rscratch::Exception.log e,request
```

An example is given below

```ruby
  def create
    begin
      @post = Post.new(params[:post])
      @post.save
      respond_to do |format|
        format.html { redirect_to @post, notice: 'Post was successfully created.' }
        format.json { render json: @post, status: :created, location: @post }
      end      
    rescue Exception => e
      # Log exception in RScratch
      Rscratch::Exception.log e,request
      
      respond_to do |format|
        format.html { redirect_to posts_path }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end            
    end
  end
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/avishekjana/rscratch. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

