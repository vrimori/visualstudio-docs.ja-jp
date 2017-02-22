---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "DISASSEMBLY_FLAGS 列挙型"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

構成のフラグを指定します。  
  
## 構文  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## メンバー  
 DF\_DOCUMENTCHANGE  
 この命令が前の値とは別のドキュメントに対して行われることを示します。  
  
 DF\_DISABLED  
 この命令が実行されないことを示します。  
  
 DF\_INSTRUCTION\_ACTIVE  
 この命令が実行される次の命令の 1 つがであることを示します \(複数存在する場合があります\)。  
  
 DF\_DATA  
 この命令が実際にデータではなくコード\) であることを示します。  
  
 DF\_HASSOURCE  
 この命令にソースがあることを示します。  一部の命令にプロファイルまたはガベージ コレクション コードなど対応するソースはありません。  
  
 DF\_DOCUMENT\_CHECKSUM  
 `bstrDocumentUrl` のフィールドがドキュメントの URL の後にチェックサムのデータが含まれていることを示します。  チェックサムのデータがどのように格納されるか [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造については" 解説 " を参照してください。  
  
## 解説  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造体の `dwFlags` のメンバーとして使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)