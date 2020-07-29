
# Today I Learned by *[José Manuel Jacobo Urzúa]*

Ruby and Rails official documentation reading personal journal

## Week 1

### Thursday 23, July 2020 *[ruby on rails installation]*
Ruby on Rails is an open source web application framework written in the Ruby programming language, following the paradigm of the Model Vista Controller model.

The ruby ​​on rails page mentions that installing rails is as easy as putting 'gem install rails' in the console, but we must bear in mind that we use the ruby ​​language and a rubygems library manager.
In my case I am working with Linux ubuntu 18.04 LTS [Install](http://rubyonrails.org.es/instala.html)

### Friday 24, July 2020 *[ruby array]*
The array in ruby ​​is the same as in other languages, it starts at 0, and when it comes to negatives like for example -1 this means the last value of your array.
To declare an array:

>ary = [1, "two", 3.0] #=> [1, "two", 3.0]
>ary = Array.new    #=> []
>Array.new(3)       #=> [nil, nil, nil]
>Array.new(3, true) #=> [true, true, true]

Elements in an array can be retrieved using the #[] method. It can take a single integer argument (a numeric index), a pair of arguments (start and length) or a range. Negative indices start counting from the end, with -1 being the last element.

>arr = [1, 2, 3, 4, 5, 6]
>arr[2]    #=> 3
>arr[100]  #=> nil
>arr[-3]   #=> 4
>arr[2, 3] #=> [3, 4, 5]
>arr[1..4] #=> [2, 3, 4, 5]
>arr[1..-3] #=> [2, 3, 4]

## Week 2

### Monday 27, July 2020 *[MVC Ruby on rails]*
This is a hint that Rails follows the model-view-controller (MVC) architectural pattern, which enforces a separation between the data in the application (such as user information) and the code used to display it, which is a common way of structuring a graphical user interface (GUI).

When interacting with a Rails application, a browser sends a request, which is received by a webserver and passed on to a Rails controller, which is in charge of what to do next. In some cases, the controller will immediately render a view, which is a template that gets converted to HTML and sent back to the browser. More commonly for dynamic sites, the controller interacts with a model, which is a Ruby object that represents an element of the site (such as a user) and is in charge of communicating with the database. After invoking the model, the controller then renders the view and returns the complete web page to the browser as HTML.

![GitHub MVC](/img/MVC.jpg)

### Thursday 28, July 2020 *[Classes, Objects, and Variables]*
In class, names always start with a capital letter, while methods start with a lowercase letter.
Each class usually contains an initialize method:

>class Song
>  def initialize(name, artist, duration)
>    @name     = name
>    @artist   = artist
>    @duration = duration
>  end
>end
initialize is a special method in Ruby programs. When you call Song.new to create a new Song object, Ruby creates an uninitialized object and then calls that object's initialize method, passing in any parameters that were passed to new. This gives you a chance to write code that sets up your object's state.

An object is an object-oriented thing that is a computer program that consists of a state and a behavior, which in turn consist respectively of stored data and tasks that can be performed at runtime.

>class KaraokeSong < Song
>  # Format ourselves as a string by appending
>  # our lyrics to our parent's #to_s value.
>  def to_s
>    super + " [#{@lyrics}]"
>  end
>end
>aSong = KaraokeSong.new("My Way", "Sinatra", 225, "And now, the...")
>aSong.to_s 	» 	"Song: My Way--Sinatra (225) [And now, the...]"

A class variable is shared among all objects of a class, and it is also accessible to the class methods that we'll describe later. There is only one copy of a particular class variable for a given class. Class variable names start with two ``at'' signs, such as ``@@count''. Unlike global and instance variables, class variables must be initialized before they are used. Often this initialization is just a simple assignment in the body of the class definition. 

>class Song
>  @@plays = 0
>  def initialize(name, artist, duration)
>    @name     = name
>    @artist   = artist
>    @duration = duration
>    @plays    = 0
>  end
>  def play
>    @plays += 1
>    @@plays += 1
>    "This  song: #@plays plays. Total #@@plays plays."
>  end
>end


### Wednesday 29, July 2020 *[Testing Rails Applications]*
Rails makes it super easy to write your tests. It starts by producing skeleton test code while you are creating your models and controllers.
By running your Rails tests you can ensure your code adheres to the desired functionality even after some major code refactoring.

Rails tests can also simulate browser requests and thus you can test your application's response without having to test it through your browser.

In the test folder of each project you will find the following folders and files:
>Drivers - Contains tests for drivers.
>fixtures - defines initial data for tests.
>helpers - contains the tests for the helpers.
>integration - contains the integration tests.
>Mailers - Contains proofs of emails.
>models - contains the model tests.
>test_helper.rb: the Minitest configuration.
