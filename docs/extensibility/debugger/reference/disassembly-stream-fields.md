---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS 列挙型"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

アセンブリのフィールドに関して取得する情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## メンバー  
 DSF\_ADDRESS  
 `bstrAddress` フィールドの初期化とを使用します。  
  
 DSF\_ADDRESSOFFSET  
 `bstrAddressOffset` フィールドの初期化とを使用します。  
  
 DSF\_CODEBYTES  
 `bstrCodeBytes` フィールドの初期化とを使用します。  
  
 DSF\_OPCODE  
 `bstrOpCode` フィールドの初期化とを使用します。  
  
 DSF\_OPERANDS  
 `bstrOperands` フィールドの初期化とを使用します。  
  
 DSF\_SYMBOL  
 `bstrSymbol` フィールドの初期化とを使用します。  
  
 DSF\_CODELOCATIONID  
 `uCodeLocationId` フィールドの初期化とを使用します。  
  
 DSF\_POSITION  
 `posBeg` と `posEnd` フィールドの初期化とを使用します。  
  
 DSF\_DOCUMENTURL  
 `bstrDocumentUrl` フィールドの初期化とを使用します。  
  
 DSF\_BYTEOFFSET  
 `dwByteOffset` フィールドの初期化とを使用します。  
  
 DSF\_FLAGS  
 `dwFlags` \(\)[DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) フィールドの初期化とを使用します。  
  
 DSF\_OPERANDS\_SYMBOLS  
 `bstrOperands` のフィールドのシンボル名を含めます。  
  
 DSF\_ALL  
 構成ストリームの場合すべてのフィールドを指定します。  
  
## 解説  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造体のフィールドが初期化する必要があるかのようにパラメーター [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) のメソッドに渡されます。  
  
 構造体が戻るときにフィールドを使用して有効かを示すために `DisassemblyData` の構造体のメンバー `dwFields` に使用されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)