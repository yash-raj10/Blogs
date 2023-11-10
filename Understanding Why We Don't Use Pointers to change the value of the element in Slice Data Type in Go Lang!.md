Ever wondered why we don't use a pointer to change the value of the element in a Slice (GO Lang) like we do with other data types like Int, String, or Struct ?

Let's have a look at the inner functioning of Slices and understand how they are working in the Background.

So when you create a slice in Go then the GO internally creates two Separate data structures for us, one is An Array (representing the actual list of items) and another is a new Slice having [ptr to head, Capacity, Length].

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wagvw0kea3larz4spnxw.jpg)
let's suppose in the RAM the new slice is stored at the address 2000 and the other data stru i.e. array (containing the actual items) is seperately stored at address 3000 and then the prt to head thing in the new slice (from 2000) is pointing to the array at 3000 and also the country var here is not pointing at the array(at 3000), it points at the new Slice at 2000 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/axqdzyizavpn80gjdlf0.jpg)
so whenever we refer to country var it's actually returning the new slice data stru, not the array & when we call a func updateCountry (used to update the list) and pass country var into it, Go still behaves as a pass by value language, and as country var points at new slice at 2000 it also makes the copy of that new Slice (at 4000) but the main thing here is that the new copy of that slice (which is at 4000) is still pointing(with the help of ptr to head) at the array of items which is at 3000 and hence in the func updateCountry when we attempt to modify the slice, we are actually modifying the same array that both copies of the slice are now pointing to(at 3000)!

And that's why we don't use a pointer to change the value of the element in a Slice

Data Stru Which acts similarly to Slices(Reference type)
~Maps
~Channels.


Dev.to link :- https://dev.to/yashraj10/understanding-why-we-dont-use-pointers-to-change-the-value-of-the-element-in-slice-data-type-in-go-lang-32fi
Hashnode link :- https://yash-raj.hashnode.dev/understanding-why-we-dont-use-pointers-to-change-the-value-of-the-element-in-slice-data-type-in-go-lang
