A SymbolDictionary that contains an Association whose key is #commitResult and whose value is one of the following Symbols: #success, #failure, #retryFailure, #commitDisallowed, or #rcFailure.

The remaining Associations in the dictionary are used to report the conflicts found.  Each Association’s key indicates the kind of conflict detected; its associated value is an Array of OOPs for the objects that are conflicting. If there are no conflicts for the transaction, the returned SymbolDictionary has no additional Associations.

The conflict sets are cleared at the beginning of a commit or abort and therefore may be examined until the next commit, continue or abort.

The keys for the conflicts are as follows:

| **Key** |                **Conflicts** |
|:--------|:-----------------------------|
|Read-Write|          StrongReadSet and WriteSetUnion conflicts|
|Write-Write|         WriteSet and WriteSetUnion conflicts|
|Write-Dependency|    WriteSet and DependencyChangeSetUnion conflicts|
|Write-WriteLock|     WriteSet and WriteLockSet conflicts|
|Write-ReadLock|      WriteSet and ReadLockSet conflicts|
|Rc-Write-Write|      Logical write-write conflict on reduced conflict object|

The Read-Write conflict set has already had RcReadSet subtracted from it.

The Write-Write conflict set does not have RcReadSet subtracted .

Beginning with Gemstone64 v1.1 , the WriteSet no longer includes objects newly committed by this transaction.  Thus a conflict between a lock and a newly committed object in prior releases will no longer show up as a conflict.

The Write-Dependency conflict set contains objects modified (including DependencyMap operations) in the current transaction that were either added to, removed from, or changed in the DependencyMap by another transaction. Objects in the Write-Dependency conflict set may be in the Write-Write conflict set.