---
title: DISASSEMBLY_STREAM_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b5c0b3f06299f9f78a6f24d8c25410a9eb4a9ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544793"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DISASSEMBLY_STREAM_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/disassembly-stream-fields)します。  
  
[逆アセンブル] フィールドの詳細を取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 初期化/使用、`bstrAddress`フィールド。  
  
 DSF_ADDRESSOFFSET  
 初期化/使用、`bstrAddressOffset`フィールド。  
  
 DSF_CODEBYTES  
 初期化/使用、`bstrCodeBytes`フィールド。  
  
 DSF_OPCODE  
 初期化/使用、`bstrOpCode`フィールド。  
  
 DSF_OPERANDS  
 初期化/使用、`bstrOperands`フィールド。  
  
 DSF_SYMBOL  
 初期化/使用、`bstrSymbol`フィールド。  
  
 DSF_CODELOCATIONID  
 初期化/使用、`uCodeLocationId`フィールド。  
  
 DSF_POSITION  
 初期化/使用、`posBeg`と`posEnd`フィールド。  
  
 DSF_DOCUMENTURL  
 初期化/使用、`bstrDocumentUrl`フィールド。  
  
 DSF_BYTEOFFSET  
 初期化/使用、`dwByteOffset`フィールド。  
  
 DSF_FLAGS  
 初期化/使用、 `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) フィールド。  
  
 DSF_OPERANDS_SYMBOLS  
 内のシンボル名を含める、`bstrOperands`フィールド。  
  
 DSF_ALL  
 [逆アセンブル] ストリームのすべてのフィールドを指定します。  
  
## <a name="remarks"></a>Remarks  
 パラメーターとして渡される、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)のどのフィールドを示すメソッド、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造体が初期化されるは。  
  
 使用、`dwFields`のメンバー、`DisassemblyData`構造体を構造体が返されるときにどのフィールドが使用し、有効なレポートを示します。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

