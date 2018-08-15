Redo Section 5.18 and the code must use dynamic array this time. All the input formats are the same.

Reference: http://www.fredosaurus.com/notes-cpp/newdelete/50dynamalloc.html

Allocate an array with code>new When the desired size of an array is known, allocate memory for it with the new operator and save the address of that memory in the pointer. Remember: Pointers may be subscripted just as arrays are. The example below reads in a number and allocates that size array.

int* a = NULL; // Pointer to int, initialize to nothing. int n; // Size needed for array cin >> n; // Read in the size a = new int[n]; // Allocate n ints and save ptr in a. for (int i=0; i<n; i++) { a[i] = 0; // Initialize all elements to zero. } . . . // Use a as a normal array delete [ ] a; // When done, free memory pointed to by a. a = NULL; // Clear a to prevent using invalid memory reference. Freeing memory with delete When you are finished with dynamically allocated memory, free it with the delete operator. After memory is freed, it can be reused by later new requests. Memory that your program didn't free will be freed when the program terminates. Never free memory that wasn't dynamically allocated - the results are unpredictable.

delete [ ] a; // Free memory allocated for the a array. a = NULL; // Be sure the deallocated memory isn't used. Use [ ] when deleting arrays You must specify "[ ]" when deleting an array, but not for a single value. It isn't possible to delete only part of an array.

Do you have to reset a pointer after delete? Following the delete in these examples, I reset the pointer to NULL. This isn't strictly necessary, but it's very good practice so that any use of the pointer will produce an error. Attempts to use memory location 0, which is the normal default value of NULL, will be blocked by the way most operating systems allocate memory.

Why doesn't delete reset the pointer? It does in some systems, but the language specification does not require it, so not all systems do it.

LAB