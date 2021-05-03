# Iteration_Exercises
Implementing the following methods:

- [x] #factors(num)
- [x] #bubble_sort!(&prc)
- [x] #bubble_sort(&prc)
- [x] #substrings(string)
- [x] #subwords(word, dictionary)
- [x] #doubler(array)
- [x] ::my_each(&prc)
- [x] ::my_map(&prc)
- [x] ::my_select(&prc)
- [x] ::my_inject(&blk)
- [x] #concatenate(strings)

To use any of these methods just download and require enumerables.rb in your file.
These are custome class methods to the Array class, implementing customer versions of 
some classic protype methods. 

#factors
  returns factors of 10 in order
  returns just two factors for primes

#subwords
  can find a simple word
  doesn't find spurious words
  can find words within words

#doubler
  doubles the elements of the array
  does not modify the original array

Array
  #bubble_sort!
    works with an empty array
    works with an array of one item
    sorts numbers
    modifies the original array
    will use a block if given
  #bubble_sort
    delegates to #bubble_sort!
    does not modify the original array
  #my_each
    calls the block passed to it
    yields each element to the block
    does NOT call the built-in #each method
    is chainable and returns the original array
  #my_map
    calls the block passed to it
    yields each element to the block
    runs the block for each element
    does NOT call the built in built-in #map method
    is chainable and returns a new array
  #my_select
    calls the block passed to it
    yields each element to the block
    returns an array of filtered down items
    does NOT call the built-in #select method
  #my_inject
    calls the block passed to it
    makes the first element the accumulator if no default is given
    yields the accumulator and each element to the block
    does NOT call the built-in #inject method
    is chainable and returns a new array

#concatenate
  returns the concatenation of the strings passed in
  does not modify the original strings
  uses the Array#inject method

```Ruby
def bubble_sort!(&prc)
    sorted = false
    prc ||= Proc.new { |a,b| a <=> b }

    while !sorted
      sorted = true

      (0...self.length - 1).each do |i|
        if prc.call(self[i], self[i+1]) == 1
          self[i], self[i+1] = self[i+1], self[i]
          sorted = false
        end
      end 
    end

    self
  end

   def my_inject(&blk)
    acc = self[0]

    self[1..-1].my_each do |ele|
      acc = blk.call(acc, ele)
    end

    acc
  end
```



