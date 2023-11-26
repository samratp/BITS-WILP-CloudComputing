Shadow Paging is recovery technique that is used to recover database. In this recovery technique, database is considered as made up of fixed size of logical units of storage which are referred as pages. pages are mapped into physical blocks of storage, with help of the page table which allow one entry for each logical page of database.

This method uses two page tables named current page table and shadow page table. The entries which are present in current page table are used to point to most recent database pages on disk. Another table i.e., Shadow page table is used when the transaction starts which is copying current page table. After this, shadow page table gets saved on disk and current page table is going to be used for transaction. Entries present in current page table may be changed during execution but in shadow page table it never get changed. After transaction, both tables become identical. This technique is also known as Cut-of-Place updating.


![image](https://github.com/samratp/BITS-WILP-CloudComputing/assets/51691541/deb35dc0-40c8-4f67-96bd-e309b69f04ec)


To understand concept, consider above figure. In this 2 write operations are performed on page 3 and 5. Before start of write operation on page 3, current page table points to old page 3. When write operation starts following steps are performed :

- Firstly, search start for available free block in disk blocks.
- After finding free block, it copies page 3 to free block which is represented by Page 3 (New).
- Now current page table points to Page 3 (New) on disk but shadow page table points to old page 3 because it is not modified.
- The changes are now propagated to Page 3 (New) which is pointed by current page table.

**COMMIT Operation** : To commit transaction following steps should be done :

- All the modifications which are done by transaction which are present in buffers are transferred to physical database.
- Output current page table to disk.
- Disk address of current page table output to fixed location which is in stable storage containing address of shadow page table. This operation overwrites address of old shadow page table. With this current page table becomes same as shadow page table and transaction is committed.

**Failure** : If system crashes during execution of transaction but before commit operation, With this, it is sufficient only to free modified database pages and discard current page table. Before execution of transaction, state of database get recovered by reinstalling shadow page table. If the crash of system occur after last write operation then it does not affect propagation of changes that are made by transaction. These changes are preserved and there is no need to perform redo operation.

**Advantages :**

- This method require fewer disk accesses to perform operation.
- In this method, recovery from crash is inexpensive and quite fast.
- There is no need of operations like- Undo and Redo.
- Recovery using this method will be faster.
- Improved fault tolerance: Shadow paging provides improved fault tolerance since it isolates transactions from each other. -This means that if one transaction fails, it does not affect the other transactions that are currently executing.
- Increased concurrency: Since modifications made during a transaction are written to the shadow copy instead of the actual database, multiple transactions can be executed concurrently without interfering with each other. This leads to increased concurrency and better performance.
- Simplicity: Shadow paging is a relatively simple technique to implement. It requires minimal modifications to the existing database system, making it easier to integrate into existing systems.
- No need for log files: In traditional database systems, log files are used to maintain a record of all changes made to the database. Shadow paging eliminates the need for log files since all changes are made to the shadow copy. This reduces the overhead associated with maintaining log files and makes the system more efficient.

**Disadvantages :**

- Due to location change on disk due to update database it is quite difficult to keep related pages in database closer on disk.
- During commit operation, changed blocks are going to be pointed by shadow page table which have to be returned to collection of free blocks otherwise they become accessible.
- The commit of single transaction requires multiple blocks which decreases execution speed.
- To allow this technique to multiple transactions concurrently it is difficult.
- Data fragmentation: The main disadvantage of this technique is the updated Data will suffer from fragmentation as the data is divided up into pages that may or not be in linear order for large sets of related hence, complex storage management strategies.
- Garbage collection: Garbage will accumulate in the pages on the disk as data is updated and pages lose any references. For example if i have a page that contains a data item X that is replaced with a new value then a new page will be created. Once the shadow page table is updated nothing will reference the old value of X. The operation to migrate between current and shadow directories must be implemented as an atomic mode.
- Performance overhead: Since modifications made during a transaction are written to the shadow copy, there is a performance overhead associated with copying the changes back to the actual database once the transaction is committed. This can impact the overall performance of the system.
- Limited concurrency control: Shadow paging does not provide strong concurrency control mechanisms. While it allows for multiple transactions to execute concurrently, it does not prevent conflicts between transactions. This means that transactions can interfere with each other, leading to inconsistencies in the database.
- Difficult to implement for some systems: Shadow paging can be difficult to implement for some systems that have complex data structures or use a lot of shared memory. In these cases, it may not be possible to maintain a shadow copy of the entire database.
- Limited fault tolerance: While shadow paging does provide improved fault tolerance in some cases, it does not provide complete fault tolerance. In the event of a crash, there is still a risk of data loss if the changes made during a transaction are not properly copied to the actual database.
