﻿# Virtual-Stack-Machine

It takes source code (in this implementation source code used is C++) and generates code in machine language which runs on a virtual stack machine. This is the function of a compiler and my implementation is that of a simple compiler.

When we do variable assignment in the E++ expressions, we don’t assign the variables a specific memory address, instead this part is handled by the compiler itself. We will maintain a vector (in a stack fashion) of available free memory indexes, delete or insert the memory index from the end if a new variable is assigned a value or it’s deleted respectively. We also assume 0-based indexing.

• compile(vector<vector<string>> code): Parses each input tokenized expression, assigns a memory mapping if the expression is a variable assignment or frees up the memory address if it’s a delete statement and finally compiles the code i.e generates and writes all the targ commands to the output file.
• generate targ commands(): Compiles the last tree node in the Parser and generates Targ commands for it and returns them.
• write to file(vector<string> commands): A helper function to write the given set of commands to the output file.

 Parameters
• Parser targ: The main object which will store the symbol table and parsed expressions tree nodes.
• int memory size: Size of the indexable memory provided to map the symbols. Set during the construction and not changed afterwards. It can be assumed that the given size of the indexable memory is always sufficient for the input set of E++ expressions
• string output file: The name of the output file in which generated Targ code needs to be dumped.
• vector<int> mem loc: A vector to maintain the available memory locations.
• MinHeap least mem loc: A min-heap to maintain the least available memory indexes
