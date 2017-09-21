Go Programming Basics
=====================
* iota only works with const ?
* number := uint8(24)
* fmt.Printf("%s\n", atoz[0:9])

Ultimage Go Programming
=======================
- Big Proyects, and thousand of line don't said anything.
- With go the abstration is small, exist but its thin.
- java, ruby, groovy base on VM, go its base on Real Machine, similar to C.
- Nothing is FREE, every decision have a cost, extra its not bad, but take in
  mind when they're needed.
- Stop copy & paste code, think on what're u doing.

Productivity vs Performance ?
------------------------------
- The important its to be productive, its fast enough?

Correctness vs Performance
--------------------------
- The Correctness of the implementation is the most important concern, but
  there is no royal road to Correctness. it involves diverses tasks such has
  thinking of invariants, testing and code reviews. Optimization should be
  done, but not prematurely.
- simple code, consistency is part of the Correctness

Code Reviews
-------------
- Integrity
        - take responsabilities, the life depends of technologies.
        - Alocate, Read, Write MEMORY.
        - less # lines of codes, its less bugs, SIMPLE.
        - Error Handling its IMPORTANT.
        - Any decision could'nt be the integrity the cause.
        - The part of ugly, large, slow its amazing.
- Readbility part of the Correctness.
        - Things like Constractors, operator overloader hide the cost.
        - Simplicity
        - Hide Complexity
        - he fight with Readbility.
        - Hide the complexity but not the cost.
        - Take more time to learn.
- Performance
- If the code its no fast enough we need to make decision and rest on
  Simplicity, Readbility but never from Integrity.
- This  should be base on Measure no guesses.
- STOP wasting effort.

Language Syntax
----------------
- Type is Life.
- 64 bits == 8 bytes.
- float64 == IEEE-754 64-bit.
- Bool == 1 byte == 8 bits.
- When he says, 'raise a flag' --> something unusual but no wrong.
- normally u dont need a int with level of precision.
- the 64 architecture means the size of the addresses are 64bits.
- word size == addresses size.
- architecture 64 == addresses 64 == word 64 == int 64.
- Playground runs on AMD64p32 == 64 architecture except for pointer?
- All the word are base on 4 bytes of memory allocation.
- Too many ways to declare variables.
- string == 2 words == empty
- var b float64 == will always be 8 bytes the arch not matter in this case.
- bool = 1 byte.
- casting could cost integrity issue, he will transform a 1 byte value to
  4 bytes value simulating the others addresses alocations.
- Go uses conversion that could resolve on a extra alocation to keep the
  integrity.
- hello == 5 bytes, 1 int this case 5, and a pointer to backend array that
  containts the world h, e, l, l, o.
### Struct Types
- You could create your own types but he don't use class but struct.
- The Struct sizes is the sum of is variables
- la imagen en el minuto 2:48 es muy buena para definir cuanto pesa el
  ejemplo.
- Because aligment boundry  there's a padding for that cost 1 extra byte.
        - bool = 1B, padding byte 1B , int16 = 2B, float32 = 4B == 7B
        - the padding its make automatic by the compiler.
        - its like a lego puzzle so a 4 byte int should bind on a 4 byte
          address, so if the int its 8 byte == 64 bits, the padding will be 7
          bytes.
        - So this could be a extra mb requirement.
        - Could be minimize defining the value on a struct from mayor to minus
          on address size.
        - type example struct {
                counter1 int64
                counter2 int64
                counter3 int64
                pi flot32
                flag1 bool
                flag2 bool
                flag3 bool
                }
        - We should do this only on the performance stage.
- Struct literal its when declaring values using := 
- Anonynous struct:
        e := struct {
		flag    bool
		counter int16
		pi      float32
	}{
		flag:    true,
		counter: 10,
		pi:      3.141592,
	}
	// Display the values.
	fmt.Printf("%+v\n", ex)
	fmt.Printf("%+v\n", e)
	fmt.Println("Flag", e.flag)
	fmt.Println("Counter", e.counter)

        - Useful when need to handle one thing only, maybe a json?
- Explicit conversions b = bill(l)
- The Explicit conversion is needed only comparing to named types no
  Anonynous types.
### Pointers
- The purpose of pointer is sharing, between program bandwidth like funtions,
  goroutines.
- The main its always running on a goroutine
- the stack size its 2K for goroutine and a piece of this stack is used to run
  a funtion call.
- By default he help the main funtion.
- The stack going down and no up.
- count == value === what's in the box.
- &count == address == where's the box.
= *valur == the value to the pointer is pointing.
- Every type declare you get a pointer for free. =)
- Every time you pass a &count you need a *type to receive the address VALUE.
	increment(&count)
        func increment(inc *int) {
	*inc++
        println("Inc:     ", *inc, &inc, inc)
        }
        ~~~~~~~~~~OUTPUT~~~~~~~~~~~~~~~
        |Beforce: 10 0x10429fa4       |
        |Inc: 11 0x10429f98 0x10429fa4|
        |Afer: 11 0x10429fa4          |
        ~~~~~~~~~~OUTPUT~~~~~~~~~~~~~~~

- The *type of Pointer will need 4 bytes == 32bits, 8 bytes == 64bits.
- In Java you always pass by reference.
- The Scape analysis will put values pass by reference on the heap because the
  stackframe for the funtion will be initialize.
        func escapeToHeap() *user {
                u := user {
                                name : "Bill",
                                email: "bill@mai.com"
                                }
                                return &u # escape analysis value to heap.
                }
- by the end the main will receive a address to the heap.
- Less preasure on the heap its more efficiency.
- To use concurrency and go routines the pointers are super needed.
-? the stackframe its no always rehuse? why the goroutine its out of memory?        with multiples funtion calls?
- If the stack need to grow to another biggest one the memory addresses move
  been copy to the new stack.
- Goroutines cannot have pointers between stacks.
- Nice exercise to grow the stack, check it out.
- If the stack consume less 25% could  reduce the size of the stack and copy
  again.
#### How the Heap works
- the pacing algorithm decide when the GC should run
- The pacing algorithm runs the GC before hit the max heap if the load hit the max
  the compiler will need to increase the heap to a minimum of 100%.
- we need to be efficient with what should be put on the heap.
- Previously when the GC start, the stop the world was required.
- On early version the stop the world not was needed but the general
  performance was reduce by 25% to all go routines that keep running.
- When the GC its running and see a GOROUTINE taking too mucho resources, he
  will pause the GOROUTINE tasks, and she will be part of the GC process.
#### Garbage Collector
- When start the Goroutines has to know that and start to use the white
  barrier and there's a Stop the world minimun.
- Root Objects == Pointer to value that are on the heap.
- Every Root found will put on a queue and check its still on use or not and
  will be marked black (in use) ir whithe( not anymore )
- The Phase II its not happening anymore.

Constants
----------
- Constants live within the compiler, and only exist at compile time.
- The Constants could have 256 bits of precision, math exacts.
- can be type and unkind
        - Untyped unkind Constants:
                const ui = 12345 // kind integer
                const uf = 3.141592 // kind floating-point.
- The untyped Constants could be implicit converter and are parts of type but
  a paralel type of system for constants.
- thye type constants cannot be implicit converter.
- we could make this with constants
        3 * 0.333 // operations between diff types, convert int to float.
- So in resume you have 2 types of constants, and could have conversion.
- iota its a operator that allow to make block of CONSTANTS with automatic
  values.
	const (
		A1 = iota // 0 : Start at 0
		B1 = iota // 1 : Increment by 1
		C1 = iota // 2 : Increment by 1
                )
- The example 3 its nice to figure out how iota works. =)

Functions
----------
- Funtions return more that 1 value.
- Go Does not have constructors.
- Factory funtions start with the word new.
- The scope for var are delimiter by {} of code.
- I must visit this topic again in the future.
- The := must declare at least 1 var and rehuse others.
- Use short variables for go because the scope.
- The _ identifier allow to not use a value if no needed.
- i like this way of defining variables to a funtion 
        // Update the user Name. Don't care about the update stats.
                if _, err := updateUser(&u); err != nil {
                        fmt.Println(err)
                        return
                }
- The first indent its the happy path the second its the negative path.
- never put inside a happy path inside of another path.

Data structures
----------------
- Slices are similar to arrays and they work on go only.
- Predictive access pattern to data ?
- Complicate topic again :/ but this are the basement of the lenguage.
- the slices are similar to vector.
- THIS COULD BE THE MORE IMPORTANT TOPIC.

Arrays
-------
- An array of string is 2 byte for each
- for the exercise the array of 5 string == 2word for each element, 10 word ==
                                                          40 bytes total
- The for range copy by value,  the value of the backend array, the fruit will
  be a string, and pointer to the same backend array and when the println
  create another copy of the backend array.
- The string don't produce garbage we always know the size of the string.
- the thing that could be on the heap its the backend array, that could
  increase with too. =)
- Type is size and representation, an array of size 4 cannot be assign to
  a array of size 5 because are different types.
- There's a amazing exercise when you can see the contiguous memory of the
  arrays.

Slices
-------
- the make its a build in funtion that works with slice, maps, channel.
- Now lets start talk about reference types, slices, maps, interfaces,
  channel, function values.
- Reference value to zero is nil != string.
- The diagrams are importants to undestand the code.
- the Slice use a diff structure type.
        3 word size, 1 pointer to backend array, 2 len, 3 cap.
- the len its what u have access to read/write.
- the cap its what's you have on the backend array
- fmt.Println(slice) this is pass by value so println get his own copy.
- this is interesting
        slice := make([]string, 5, 8) //defining the len, and extra capacity.
- Off couse you could declare the max of a slice but do it only when its
  needed, after testing, remember Correctness.
- its possible to use a empty struct that return empty instead of null
- with var you always return zero values.
- build in function append allow you add values to the slice, making the slice
  dynamic, without loosing contiguous address.
-  the append will copy the value a bring another new copy of the slide.
- its possible the slice of a slice with [a:b] but could be confuse the best
  way is using [2:3] when 2 its the position of what i want and the other is
  the total len.
- When we change a value of a backend array that who its the pointer value to
  several slides, all the slides will change.
- The solution would be put a new slice from a slice but with similar len and
  capacity, this way need to create a new allocation to the array.
- slice of slices == slicing.
- The thing is if you put a pointer to a slice then and need to allocate a new
backend array you lost your pointer, the value its on another address.
- Chinese character need 3byte of data for each one.
- copy its a buildin function, works for string and slices, string could be
  a source, a slice could be a source & destination.
- the for range iterate between code point no bytes.
