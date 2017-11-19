---
title: "CONTEXT_INFO_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e604dc09215ac98b2c23fe85312e281b306e9961
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
メモリのコンテキストに関するを取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>メンバー  
 CIF_MODULEURL  
 初期化/を使用して、`bstrModuleUrl`のフィールド、 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)構造体。  
  
 CIF_FUNCTION  
 初期化/を使用して、`bstrFunction`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_FUNCTIONOFFSET  
 初期化/を使用して、`posFunctionOffset`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ADDRESS  
 初期化/を使用して、`bstrAddress`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ADDRESSOFFSET  
 初期化/を使用して、`bstrAddressOffset`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ALLFIELDS  
 すべてのフィールドを使用して初期化、`CONTEXT_INFO`構造体。  
  
## <a name="remarks"></a>コメント  
 これらの値がパラメーターに渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)メソッドのどのフィールドを示すために、 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)構造が初期化するのには。  
  
 これらのフラグはのどのフィールドを示すためにも使用、`CONTEXT_INFO`構造が返されるときに構造体が使用される、有効です。  
  
 これらの値は、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)