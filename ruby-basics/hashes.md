!SLIDE subsection
# Hash

Ref. WGR Chapter 9, Section 9.3, Hashes

# Hash

* also known as...
  * Map
  * Associative Array
  * Dictionary
  * Name/Value Pair Store
  * Key/Value Pair Store
  
# Hash literal

a Hash can be defined *literally* (inline) with braces e.g.

    @@@ ruby
    states = {"MA" => "Massachusetts",
              "CA" => "California"}

    states["MA"] #=> "Massachusetts"

!SLIDE

    @@@ ruby
    my_hash = {:a_symbol => 3, "a string" => 4}
    my_hash[:a_symbol] #=> 3
    
    my_hash[:foo] = "bar"
    my_hash #=> {:a_symbol => 3, "a string" => 4, :foo => "bar"}
    

# Hash literals

Ruby 1.8 or 1.9:

    {:foo => "bar", :baz => "baf"}

Ruby 1.9 only:

    {foo: "bar", baz: "baf"}

# hash parameters plus hash literals => named parameters

These are all equivalent:

    @@@ruby
    User.new({:name => "Alex", :email => "alex@stinky.com"})
    User.new(:name => "Alex", :email => "alex@stinky.com")
    User.new :name => "Alex", :email => "alex@stinky.com"
    User.new name: "Alex", email: "alex@stinky.com"
    User.new name:"Alex", email:"alex@stinky.com"
    User.new email:"alex@stinky.com", name:"Alex"

# Hash access

    hash[:foo] = "bar"
    hash[:foo] #=> "bar"

# Hash methods

* each, each_pair
* keys, values
* has_key?, has_value?
* merge, merge!
* delete, delete_if
  
  `delete` is good when we are passing huge number of hashes around the class or objects. Good part is that when we do
  `my_hash.delete(:foo)` Deletes the key-value pair and returns the value from hsh whose key is equal to key. If the key is not found, returns the default value. This keeps hashes clean once used so they are delete for good after use. Just use and thow
* assert_key_values
  `assert_key_values` gives you the ability to verify that each of the keys in the Hash are expected. For example, if you take an options Hash as an argument to a method you may want to validate that only expected options are passed as part of the hash; assert_valid_keys gives you the ability to list the keys you expect.

# Hash arguments

braces are optional...

...**if** the hash is the final argument

(except for a default block)

# `merge` to combine two hashes

Here's a handy trick:

    class Hash
      alias_method :<<, :merge!
      alias_method :+, :merge
    end

    {foo: 1} << {bar: 2}
    => {:foo=>1, :bar=>2}   # destructive

    {foo: 1} + {bar: 2}
    => {:foo=>1, :bar=>2}   # creative


