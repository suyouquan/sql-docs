---
title: "Rowset Properties and Behaviors | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "docset-sql-devref"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "rowsets [OLE DB], properties"
  - "SQL Server Native Client OLE DB provider, rowsets"
  - "properties [OLE DB]"
  - "OLE DB rowsets, properties"
ms.assetid: 9baabcb6-0114-42f2-89f8-d8d66b3c8c14
caps.latest.revision: 47
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Rowset Properties and Behaviors
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  These are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowset properties.  
  
|Property ID|Description|  
|-----------------|-----------------|  
|DBPROP_ABORTPRESERVE|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The behavior of a rowset after an abort operation is determined by this property.<br /><br /> VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider invalidates rowsets after an abort operation. Functionality of the rowset object is almost lost. It supports only **IUnknown** operations and the release of outstanding row and accessor handles.<br /><br /> VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider maintains a valid rowset.|  
|DBPROP_ACCESSORDER|R/W: Read/write<br /><br /> Default: DBPROPVAL_AO_RANDOM<br /><br /> Description: Access order. Order in which columns must be accessed on the rowset.<br /><br /> DBPROPVAL_AO_RANDOM: Column can be accessed in any order.<br /><br /> DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS: Columns bound as storage objects can only be accessed in sequential order determined by the column ordinal.<br /><br /> DBPROPVAL_AO_SEQUENTIAL: All columns must be accessed in sequential order determined by column ordinal.|  
|DBPROP_APPENDONLY|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider storage objects block using other rowset methods.|  
|DBPROP_BOOKMARKS DBPROP_LITERALBOOKMARKS|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports bookmarks for rowset row identification when DBPROP_BOOKMARKS or DBPROP_LITERALBOOKMARKS is VARIANT_TRUE.<br /><br /> Setting either property to VARIANT_TRUE does not enable rowset positioning by bookmark. Set DBPROP_IRowsetLocate or DBPROP_IRowsetScroll to VARIANT_TRUE to create a rowset supporting rowset positioning by bookmark.<br /><br /> The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor to support a rowset that contains bookmarks. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> Note: Setting these properties in conflict with other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-defining properties causes an error. For example, setting the DBPROP_BOOKMARKS to VARIANT_TRUE when DBPROP_OTHERINSERT is also VARIANT_TRUE generates an error when the consumer tries to open a rowset.|  
|DBPROP_BOOKMARKSKIPPED|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_E_BADBOOKMARK if the consumer indicates an invalid bookmark when positioning or searching a bookmarked rowset.|  
|DBPROP_BOOKMARKTYPE|R/W: Read-only<br /><br /> Default: DBPROPVAL_BMK_NUMERIC<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements numeric bookmarks only. A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider bookmark is 32-bit unsigned integer, type DBTYPE_UI4.|  
|DBPROP_CACHEDEFERRED|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_CANFETCHBACKWARDS DBPROP_CANSCROLLBACKWARDS|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports backward fetching and scrolling in nonsequential rowsets. The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates a cursor-supported rowset when either DBPROP_CANFETCHBACKWARDS or DBPROP_CANSCROLLBACKWARDS is VARIANT_TRUE. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_CANHOLDROWS|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_E_ROWSNOTRELEASED if the consumer tries to obtain more rows for a rowset while pending changes exist on those currently in the rowset. This behavior can be modified.<br /><br /> Setting both DBPROP_CANHOLDROWS and DBPROP_IRowsetChange to VARIANT_TRUE implies a bookmarked rowset. If both properties are VARIANT_TRUE, the **IRowsetLocate** interface is available on the rowset and DBPROP_BOOKMARKS and DBPROP_LITERALBOOKMARKS are both VARIANT_TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets that contain bookmarks are supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.|  
|DBPROP_CHANGEINSERTEDROWS|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: This property can only be set to VARIANT_TRUE if the rowset is using a keyset-driven cursor.|  
|DBPROP_COLUMNRESTRICT|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets the property to VARIANT_TRUE when a column in a rowset cannot be changed by the consumer. Other columns in the rowset may be updatable and the rows themselves may be deleted.<br /><br /> When the property is VARIANT_TRUE, the consumer examines the *dwFlags* member of the DBCOLUMNINFO structure to determine whether the value of an individual column can be written or not. For modifiable columns, *dwFlags* exhibits DBCOLUMNFLAGS_WRITE.|  
|DBPROP_COMMANDTIMEOUT|R/W: Read/write<br /><br /> Default: 0<br /><br /> Description: By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not time out on the **ICommand::Execute** method.|  
|DBPROP_COMMITPRESERVE|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The behavior of a rowset after a commit operation is determined by this property.<br /><br /> VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider maintains a valid rowset.<br /><br /> VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider invalidates rowsets after a commit operation. Functionality of the rowset object is almost lost. It supports only **IUnknown** operations and the release of outstanding row and accessor handles.|  
|DBPROP_DEFERRED|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: When set to VARIANT_TRUE the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to use a server cursor for the rowset. **Text**, **ntext**, and **image** columns are not returned from the server until they are accessed by the application.|  
|DBPROP_DELAYSTORAGEOBJECTS|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports immediate update mode on storage objects.<br /><br /> Changes made to data in a sequential stream object are immediately submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Modifications are committed based on the rowset transaction mode.|  
|DBPROP_HIDDENCOLUMNS|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> **Description:** Hidden Column Count<br /><br /> If DBPROP_UNIQUEROWS is VARIANT_TRUE, the DBPROP_HIDDENCOLUMNS property returns the number of additional "hidden" columns added by the provider to uniquely identify rows within the rowset. These columns are returned by **IColumnsInfo::GetColumnInfo** and **IColumnsRowset::GetColumnsRowset**. However, they are not included in the count of rows returned by the *pcColumns* argument returned by **IColumnsInfo::GetColumnInfo**.<br /><br /> To determine the total number of columns represented in the *prgInfo* structure returned by **IColumnsInfo::GetColumnInfo**, including hidden columns, the consumer adds the value of DBPROP_HIDDENCOLUMNS to the count of columns returned from **IColumnsInfo::GetColumnInfo** in *pcColumns*. If DBPROP_UNIQUEROWS is VARIANT_FALSE, DBPROP_HIDDENCOLUMNS is zero.|  
|DBPROP_IAccessor DBPROP_IColumnsInfo DBPROP_IConvertType DBPROP_IRowset DBPROP_IRowsetInfo|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports these interfaces on all rowsets.|  
|DBPROP_IColumnsRowset|R/W: Read/write<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IColumnsRowset** interface.|  
|DBPROP_IConnectionPointContainer|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: IConnectionPointContainer. If VARIANT_TRUE, the rowset supports the specified interface. If VARIANT_FALSE, the rowset does not support the specified interface. Providers that support an interface must support the property associated with that interface with a value of VARIANT_TRUE. These properties are primarily used to request interfaces through ICommandProperties::SetProperties.|  
|DBPROP_IMultipleResults|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IMultipleResults** interface.|  
|DBPROP_IRowsetChange DBPROP_IRowsetUpdate|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IRowsetChange** and **IRowsetUpdate** interfaces.<br /><br /> A rowset created by using DBPROP_IRowsetChange equal to VARIANT_TRUE exhibits immediate update mode behaviors.<br /><br /> When DBPROP_IRowsetUpdate is VARIANT_TRUE, DBPROP_IRowsetChange is also VARIANT_TRUE. The rowset exhibits delayed update mode behavior.<br /><br /> The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor to support rowsets exposing either **IRowsetChange** or **IRowsetUpdate**. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_IRowsetIdentity|R/W: Read/write<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IRowsetIdentity** interface. If a rowset supports this interface, any two row handles representing the same underlying row will always reflect the same data and state. Consumers can call the **IRowsetIdentity:: IsSameRow** method to compare two row handles to see if they refer to the same row instance.|  
|DBPROP_IRowsetLocate DBPROP_IRowsetScroll|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can expose the **IRowsetLocate** and **IRowsetScroll** interfaces.<br /><br /> When DBPROP_IRowsetLocate is VARIANT_TRUE, DBPROP_CANFETCHBACKWARDS and DBPROP_CANSCROLLBACKWARDS are also VARIANT_TRUE.<br /><br /> When DBPROP_IRowsetScroll is VARIANT_TRUE, DBPROP_IRowsetLocate is also VARIANT_TRUE, and both interfaces are available on the rowset.<br /><br /> Bookmarks are required for either interface. The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets DBPROP_BOOKMARKS and DBPROP_LITERALBOOKMARKS to VARIANT_TRUE when the consumer requests either interface.<br /><br /> The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support **IRowsetLocate** and **IRowsetScroll**. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> Setting these properties in conflict with other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cursor-defining properties causes an error. For example, setting DBPROP_IRowsetScroll to VARIANT_TRUE when DBPROP_OTHERINSERT is also VARIANT_TRUE generates an error when the consumer tries to open a rowset.|  
|DBPROP_IRowsetResynch|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IRowsetResynch** interface on demand. The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can expose the interface on any rowset.|  
|DBPROP_ISupportErrorInfo|R/W: Read/write<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISupportErrorInfo** interface on rowsets.|  
|DBPROP_ILockBytes|This interface is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property generates an error.|  
|DBPROP_ISequentialStream|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ISequentialStream** interface to support long, variable-length data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBPROP_IStorage|This interface is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property generates an error.|  
|DBPROP_IStream|This interface is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property generates an error.|  
|DBPROP_IMMOBILEROWS|R/W: Read/write<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The property is only VARIANT_TRUE for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keyset cursors; it is VARIANT_FALSE for all other cursors.<br /><br /> VARIANT_TRUE: The rowset will not reorder the inserted or updated rows. For **IRowsetChange::InsertRow**, rows will appear at the end of the rowset. For **IRowsetChange::SetData**, if the rowset is not ordered, the position of the updated rows is not changed. If the rowset is ordered and **IRowsetChange::SetData** changes a column that is used to order the rowset, the row is not moved. If the rowset is built on a set of key columns (typically a rowset for which DBPROP_OTHERUPDATEDELETE is VARIANT_TRUE but DBPROP_OTHERINSERT is VARIANT_FALSE), changing the value of a key column is generally equivalent to deleting the current row and inserting a new one. Therefore, the row may appear to move or even disappear from the rowset, if DBPROP_OWNINSERT is VARIANT_FALSE, even though the DBPROP_IMMOBILEROWS property is VARIANT_TRUE.<br /><br /> VARIANT_FALSE: If the rowset is ordered, inserted rows appear in the rowset's correct order. If the rowset is not ordered, the inserted row appears at the end. If **IRowsetChange::SetData** changes a column that is used to order the rowset, the row is moved. If the rowset is not ordered, the position of the row is not changed.|  
|DBPROP_LITERALIDENTITY|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: This property is always VARIANT_TRUE.|  
|DBPROP_LOCKMODE|R/W: Read/write<br /><br /> Default: DBPROPVAL_LM_NONE<br /><br /> Description: Level of locking performed by the rowset (DBPROPVAL_LM_NONE, DBPROPVAL_LM_SINGLEROW).<br /><br /> Note: When using snapshot isolation in a transaction, if a rowset is opened by using a keyset or dynamic server cursor and the lock mode is set to DBPROPVAL_LM_SINGLEROW, an error will occur when fetching a row if someone else has updated that row since the transaction was started. For other cursor types and lock modes, if someone else has updated the row since the transaction was started, an error does not occur until the user tries to update the row. In both cases, these errors are generated by the server.|  
|DBPROP_MAXOPENROWS|R/W: Read-only<br /><br /> Default: 0<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not limit the number of rows that can be active in rowsets.|  
|DBPROP_MAXPENDINGROWS|R/W: Read-only<br /><br /> Default: 0<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not limit the number of rowset rows with changes pending.|  
|DBPROP_MAXROWS|R/W: Read/write<br /><br /> Default: 0<br /><br /> Description: By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not limit the number of rows in a rowset. When the consumer sets DBPROP_MAXROWS, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the SET ROWCOUNT statement to limit the number of rows in the rowset.<br /><br /> SET ROWCOUNT can cause unintended consequences in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statement execution. For more information, see [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md).|  
|DBPROP_MAYWRITECOLUMN|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_MEMORYUSAGE|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_NOTIFICATIONGRANULARITY|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_NOTIFICATIONPHASES|R/W: Read-only<br /><br /> Default: DBPROPVAL_NP_OKTODO &#124; DBPROPVAL_NP_ABOUTTODO &#124;  DBPROPVAL_NP_SYNCHAFTER &#124; DBPROPVAL_NP_FAILEDTODO &#124;  DBPROPVAL_NP_DIDEVENT<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all notification phases.|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|R/W: Read-only<br /><br /> Default: DBPROPVAL_NP_OKTODO &#124;  DBPROPVAL_NP_ABOUTTODO<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider notification phases are cancelable before an attempt to perform the rowset modification indicated. The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support phase cancellation after the attempt has completed.|  
|DBPROP_ORDEREDBOOKMARKS|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE DBPROP_OWNINSERT DBPROP_OWNUPDATEDELETE|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: Setting change visibility properties causes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_QUICKRESTART|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: When set to VARIANT_TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to use a server cursor for the rowset.|  
|DBPROP_REENTRANTEVENTS|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets are re-entrant and can return DB_E_NOTREENTRANT if a consumer tries to access a nonre-entrant rowset method from a notification callback.|  
|DBPROP_REMOVEDELETED|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider alters the value of the property based on the visibility of changes to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data exposed by the rowset.<br /><br /> VARIANT_TRUE: Rows deleted by the consumer or other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] users are removed from the rowset when the rowset is refreshed. DBPROP_OTHERINSERT is VARIANT_TRUE.<br /><br /> VARIANT_FALSE: Rows deleted by the consumer or other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] users are not removed from the rowset when the rowset is refreshed. The row status value for deleted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rows in the rowset is DBROWSTATUS_E_DELETED. DBPROP_OTHERINSERT is VARIANT_TRUE.<br /><br /> This property only has value for rowsets supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> When the DBPROP_REMOVEDELETED property is implemented on a keyset cursor rowset, deleted rows are removed at fetch time and it is possible for row-fetching methods, such as **GetNextRows** and **GetRowsAt,** to return both S_OK and fewer rows than requested. Note that this behavior does not signify the DB_S_ENDOFROWSET condition and that the number of rows returned will never be zero if there are any remaining rows.|  
|DBPROP_REPORTMULTIPLECHANGES|This rowset property is not implemented by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider. Trying to read or write the property value generates an error.|  
|DBPROP_RETURNPENDINGINSERTS|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: When a method that fetches rows is called, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not return pending insert rows.|  
|DBPROP_ROWRESTRICT|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets do not support access rights based on the row. If the **IRowsetChange** interface is exposed on a rowset, the **SetData** method can be called by the consumer.|  
|DBPROP_ROWSET_ASYNCH|R/W: Read/write<br /><br /> Default: 0<br /><br /> Description: Provides for anychronous rowset processing. This property is in the Rowset property group and DBPROPSET_ROWSET property set. Type is VT_14.<br /><br /> The only value in the bitmask supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is **DBPROPVAL_ASYNCH_INITIALIZE**.|  
|DBPROP_ROWTHREADMODEL|R/W: Read-only<br /><br /> Default: DBPROPVAL_RT_FREETHREAD<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports access to its objects from multiple execution threads of a single consumer.|  
|DBPROP_SERVERCURSOR|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: When set, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor is used to support the rowset. For more information, see [Rowsets and SQL Server Cursors](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_SERVERDATAONINSERT|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: Server data on insert.<br /><br /> VARIANT_TRUE: At the time an insert is transmitted to the server, the provider retrieves data from the server to update the local row cache.<br /><br /> VARIANT_FALSE: The provider does not retrieve server values for newly inserted rows.|  
|DBPROP_STRONGIDENTITY|R/W: Read-only<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: Strong row identity. If inserts are allowed on a rowset (either **IRowsetChange** or **IRowsetUpdate** is true), and DBPROP_UPDATABILITY is set to support InsertRows, the value of DBPROP_STRONGIDENTITY depends on DBPROP_CHANGEINSERTEDROWS property (will be VARIANT_FALSE if DBPROP_CHANGEINSERTEDROWS property value is VARIANT_FALSE).|  
|DBPROP_TRANSACTEDOBJECT|R/W: Read-only<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports only transacted objects. For more information, see [Transactions](../../relational-databases/native-client-ole-db-transactions/transactions.md).|  
|DBPROP_UNIQUEROWS|R/W: Read/write<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: Unique rows.<br /><br /> VARIANT_TRUE: Each row is uniquely identified by its column values. The set of columns which uniquely identify the row have the DBCOLUMNFLAGS_KEYCOLUMN set in the DBCOLUMNINFO structure returned from the **GetColumnInfo** method.<br /><br /> VARIANT_FALSE: Rows may or may not be uniquely identified by their column values. The key columns may or may not be flagged with DBCOLUMNFLAGS_KEYCOLUMN.|  
|DBPROP_UPDATABILITY|R/W: Read/write<br /><br /> Default: 0<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all DBPROP_UPDATABILITY values. Setting DBPROP_UPDATABILITY does not create a modifiable rowset. To make a rowset modifiable, set DBPROP_IRowsetChange or DBPROP_IRowsetUpdate.|  
  
 The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the provider-specific property set DBPROPSET_SQLSERVERROWSET as shown in this table.  
  
|Property ID|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMN_ID|Column: ColumnID<br /><br /> R/W: Read-only<br /><br /> Type: VT_U12 &#124; VT_ARRAY<br /><br /> Default: VT_EMPTY<br /><br /> Description: An array of integer values representing the ordinal position (1-based) of a COMPUTE clause result column within the current [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement. This is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider equivalent of the ODBC SQL_CA_SS_COLUMN_ID attribute.|  
|SSPROP_DEFERPREPARE|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_BOOL<br /><br /> Default: VARIANT_TRUE<br /><br /> Description: VARIANT_TRUE: In prepared execution, the command preparation is deferred until **ICommand::Execute** is called or a metaproperty operation is performed. If the property is set to<br /><br /> VARIANT_FALSE: The statement is prepared when **ICommandPrepare::Prepare** is executed.|  
|SSPROP_IRowsetFastLoad|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_BOOL<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: Set this property to VARIANT_TRUE to open a fast load rowset through **IOpenRowset::OpenRowset**. You cannot set this property in **ICommandProperties::SetProperties**.|  
|SSPROP_ISSAsynchStatus|Column: No.<br /><br /> R/W: Read/write<br /><br /> Type: VT_BOOL<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: Set this property to VARIANT_TRUE to enable asynchronous operations using the [ISSAsynchStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md) interface.|  
|SSPROP_MAXBLOBLENGTH|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_I4<br /><br /> Default: The provider does not restrict the size of the text returned by the server and the property value is set to its maximum. For example, 2147483647.<br /><br /> Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider executes a SET TEXTSIZE statement to restrict the length of binary large object (BLOB) data returned in a SELECT statement.|  
|SSPROP_NOCOUNT_STATUS|Column: NoCount<br /><br /> R/W: Read-only<br /><br /> Type: VT_BOOL<br /><br /> Default: VARIANT_FALSE<br /><br /> Description: A boolean value representing the status of SET NOCOUNT ON/OFF in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> VARIANT_TRUE: when SET NOCOUNT ON<br /><br /> VARIANT_FALSE: when SET NOCOUNT OFF|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_BSTR (1-2000 characters allowed)<br /><br /> Default: Empty string<br /><br /> Description: The message text of the query notification. This is user defined, and has no defined format.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_BSTR<br /><br /> Default: Empty string<br /><br /> Description: The query notification options. These are specified in a string with `name=value`. The user is responsible for creating the service and reading notifications off of the queue. The syntax of the query notifications options string is:<br /><br /> `service=<service-name>[;(local database=<database>&#124;broker instance=<broker instance>)]`<br /><br /> For example:<br /><br /> `service=mySSBService;local database=mydb`|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|Column: No<br /><br /> R/W: Read/write<br /><br /> Type: VT_UI4<br /><br /> Default: 432000 seconds (5 days)<br /><br /> Minimum: 1 seconds<br /><br /> Maximum: 2^31-1 seconds<br /><br /> Description: The number of seconds that the query notification is to remain active.|  
  
## See Also  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  