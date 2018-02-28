---
title: "DISASSEMBLY_STREAM_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1629e2665d3b02bebba35583561df49d6fdac221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
[逆アセンブル] フィールドの詳細を取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
## <a name="members"></a>メンバー  
 DSF_ADDRESS  
 初期化/を使用して、`bstrAddress`フィールドです。  
  
 DSF_ADDRESSOFFSET  
 初期化/を使用して、`bstrAddressOffset`フィールドです。  
  
 DSF_CODEBYTES  
 初期化/を使用して、`bstrCodeBytes`フィールドです。  
  
 DSF_OPCODE  
 初期化/を使用して、`bstrOpCode`フィールドです。  
  
 DSF_OPERANDS  
 初期化/を使用して、`bstrOperands`フィールドです。  
  
 DSF_SYMBOL  
 初期化/を使用して、`bstrSymbol`フィールドです。  
  
 DSF_CODELOCATIONID  
 初期化/を使用して、`uCodeLocationId`フィールドです。  
  
 DSF_POSITION  
 初期化/を使用して、`posBeg`と`posEnd`フィールドです。  
  
 DSF_DOCUMENTURL  
 初期化/を使用して、`bstrDocumentUrl`フィールドです。  
  
 DSF_BYTEOFFSET  
 初期化/を使用して、`dwByteOffset`フィールドです。  
  
 DSF_FLAGS  
 初期化/を使用して、 `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) フィールドです。  
  
 DSF_OPERANDS_SYMBOLS  
 シンボル名を含む、`bstrOperands`フィールドです。  
  
 DSF_ALL  
 [逆アセンブル] ストリームのすべてのフィールドを指定します。  
  
## <a name="remarks"></a>コメント  
 パラメーターとして渡される、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)メソッドのどのフィールドを示すために、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造が初期化するのには。  
  
 使用、`dwFields`のメンバー、`DisassemblyData`を示すためにどのフィールドに使用されると有効な構造が返される構造体。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)