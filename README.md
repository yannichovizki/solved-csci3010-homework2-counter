Download Link: https://assignmentchef.com/product/solved-csci3010-homework2-counter
<br>



<strong>Objectives:</strong>

<ul>

 <li>Implement generalized c++ functions/classes</li>

 <li>Use “mini” c++ topics that we have covered: const, overloading, unit testing – Design and implement unit tests for a templated class</li>

</ul>

<strong>Turn in: </strong>

<ul>

 <li>hpp, test.cpp, Makefile. You are not required to turn in main.cpp though you are highly encouraged to write a main as you test your Counter object! You do not need to turn in catch.hpp.</li>

</ul>

<strong>Instructions: </strong>

Your job is to implement a templated Counter class in C++. A Counter is a specialized type of map (dictionary) that counts the occurrences of hashable objects. You can think of it as a version of a std::map&lt;T, int&gt; with a fancy interface. For our Counter&lt;T&gt;, counts are allowed to be any positive integer value or 0. If you do not have experience working with c++ maps, see the end of this write-up for examples to get started.




If you find writing a main.cpp helpful, you may do so but this is not required.




Your Counter&lt;T&gt; class must provide the following interface:




<table width="719">

 <tbody>

  <tr>

   <td width="368"><u>Function Signatures</u>Note: it is your job to determine which parameters and methods should be const!</td>

   <td width="351"><u>Description of behavior</u></td>

  </tr>

  <tr>

   <td width="368">Counter(); Counter(std::vector&lt;T&gt; vals);</td>

   <td width="351">initialize an empty Counter&lt;T&gt; initialize a Counter&lt;T&gt; appropriately from a vector or array that contains type T</td>

  </tr>

  <tr>

   <td width="368">int Count();   int Count(T key);   int Count(T min, T max);</td>

   <td width="351">access the total of all counts so far  access the count associated with any object T, even for values of T that have not been counted access the total of all counts for objects T given a certain range (an inclusive minimum T and an exclusive maximum T element)</td>

  </tr>

  <tr>

   <td width="368">void Remove(T key)</td>

   <td width="351">remove all counts of an object T from the Counter</td>

  </tr>

  <tr>

   <td width="368">void Increment(T key); void Increment(T key, int n);</td>

   <td width="351">increment the count of an object T by one increment the count of an object T by n</td>

  </tr>

 </tbody>

</table>




<table width="719">

 <tbody>

  <tr>

   <td width="368">void Decrement(T key); void Decrement(T key, int n);</td>

   <td width="351">decrement the count of an object T by one decrement the count of an object T by n</td>

  </tr>

  <tr>

   <td width="368">T MostCommon();       std::vector&lt;T&gt; MostCommon(int n);</td>

   <td width="351">get the most commonly occurring object of type T(the object with the highest count)If the Counter is empty, this method should throw a <a href="https://en.cppreference.com/w/cpp/error/domain_error">domain error</a>   get the n most commonly occurring objects of type T. If the Counter is empty, this method should return a vector of size 0. *clarification (2/19/2020)*When breaking ties, your Counter should return the first element in the Counter at the given place.Example:if your Counter contains {“cat”:2, “dog”: 2, “kangaroo”: 3, “salamander”:1}, thenMostCommon() -&gt; returns “kangaroo”MostCommon(2) -&gt; returns “kangaroo”, “cat” (in any order)MostCommon(3) -&gt; returns “kangaroo”, “cat”, “dog”(in any order)MostCommon(4) -&gt; returns “kangaroo”, “cat”,“dog”, “salamander” (in any order)</td>

  </tr>

  <tr>

   <td width="368">T LeastCommon();     std::vector&lt;T&gt; LeastCommon(int n);</td>

   <td width="351">get the least commonly occurring object of type T(the object with the highest count)If the Counter is empty, this method should throw a <a href="https://en.cppreference.com/w/cpp/error/domain_error">domain error</a>  get the n least commonly occurring objects of type Tget the n most commonly occurring objects of type T. If the Counter is empty, this method should return a vector of size 0. *clarification (2/19/2020)*When breaking ties, your Counter should return the first element in the Counter at the given place.</td>

  </tr>

  <tr>

   <td width="368"></td>

   <td width="351">Example:if your Counter contains {“cat”:2, “dog”: 2, “kangaroo”: 3, “salamander”:1}, thenLeastCommon() -&gt; returns “salamander”LeastCommon(2) -&gt; returns “salamander”, “cat” (in any order)LeastCommon(3) -&gt; returns “salamander”, “cat”, “dog” (in any order)MostCommon(4) -&gt; returns “salamander”, “cat”,“dog”, “kangaroo” (in any order)</td>

  </tr>

  <tr>

   <td width="368">std::map&lt;T, double&gt; Normalized();</td>

   <td width="351">access normalized weights for all objects of type T seen so far○    normalized weights means that each value of type T would be associated with the percentage of all items of type T that have been counted that are that value○    it essentially converts each T, int pair to a T, double pair where the double is the percentage rather than the raw count ○    Say that you have a Counter&lt;std::string&gt; which contains the data:–       {“cat”: 8, “dog”: 4, “hamster”: 2,“eagle”: 6}–       a map of normalized weights wouldbe: {“cat”: 0.4, “dog”: 0.2, “hamster”:0.1, “eagle”: 0.3}</td>

  </tr>

  <tr>

   <td width="368">std::set&lt;T&gt; Keys();</td>

   <td width="351">access the set of all keys in the Counter</td>

  </tr>

  <tr>

   <td width="368">std::vector&lt;int&gt; Values();</td>

   <td width="351">access the collection of all values in the Counter</td>

  </tr>

  <tr>

   <td width="368">  std::ostream&amp; operator&lt;&lt;(std::ostream&amp; os, const Counter&lt;U&gt; &amp;b);</td>

   <td width="351">overload the &lt;&lt; operator for Counter&lt;T&gt; This should print out the contents of the Counter in the format: {T: count, T: count, T: count, …, T:count}</td>

  </tr>

 </tbody>

</table>













<strong><u>Counter&lt;T&gt; and different types:</u> </strong>

Your Counter&lt;T&gt; must work for types T that are new, custom types, such as programmer-defined structs and classes. Each method that you implement must be adequately tested. You do not need to test each method with a Counter&lt;T&gt; of every type that T could be (that would be impossible!), but your different TEST_CASEs should make use of Counters that hold a variety of different types.




See examples <a href="https://github.com/muzny/csci3010-cuboulder/tree/master/examples">in the examples folde</a>​  <a href="https://github.com/muzny/csci3010-cuboulder/tree/master/examples">r</a> on github for how to write templated classes and functions, as well as the​         resources linked to<a href="https://github.com/muzny/csci3010-cuboulder/blob/master/resources.md#templating"> in the resources document</a><u>​           </u><a href="https://github.com/muzny/csci3010-cuboulder/blob/master/resources.md#templating">.</a>




We are happy to clarify any methods/requirements that you’d like guidance on, so please, make sure to ask if you have any questions.

<strong> </strong>

<strong>As always, your functions should be well documented. Since a main.cpp is not required, include your file comment with your name(s) and instructions for running your program in test.cpp. </strong>

<strong> </strong>

<strong><u>Some thoughts on getting started:</u> </strong>

Though you may have the inclination to start by writing a non-templated version of your Counter and then converting it, our experience has been that getting a templated class started in c++ can be difficult enough that this might make finding your compiler issues harder. Therefore, we recommend the following steps:

<ul>

 <li>Define your Counter&lt;T&gt; class with just a constructor.</li>

 <li>Make sure you can create a Counter&lt;int&gt; (or some other primitive/built in type).</li>

 <li>Write unit tests for one of the Counter&lt;T&gt; methods</li>

 <li>Implement the Counter&lt;T&gt; method</li>

 <li>Run your tests</li>

 <li>Go back to step 3 and repeat until complete</li>

</ul>


