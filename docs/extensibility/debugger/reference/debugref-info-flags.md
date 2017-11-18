---
title: "DEBUGREF_INFO_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUGREF_INFO_FLAGS
helpviewer_keywords: DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6022173da00b42272c0b03d5a9a2e2c83f6fb890
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Debug 参照オブジェクトの概要を取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 DEBUGREF_INFO_NAME  
 初期化/を使用して、`bstrName`構造体のフィールドです。  
  
 DEBUGREF_INFO_TYPE  
 初期化/を使用して、`bstrType`構造体のフィールドです。  
  
 DEBUGREF_INFO_VALUE  
 初期化/を使用して、`bstrValue`構造体のフィールドです。  
  
 DEBUGREF_INFO_ATTRIB  
 初期化/を使用して、`dwAttrib`構造体のフィールドです。  
  
 DEBUGREF_INFO_REFTYPE  
 初期化/を使用して、`dwRefType`構造体のフィールドです。  
  
 DEBUGREF_INFO_REF  
 初期化/を使用して、`pReference`構造体のフィールドです。  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 [値] フィールドは、使用可能なこの種類のオブジェクトの場合、自動拡張値を含める必要があります。  
  
 DEBUGREF_INFO_NONE  
 フラグが設定されていないことを示します。  
  
 DEBUGREF_INFO_ALL  
 フラグのマスクを示します。  
  
## <a name="remarks"></a>コメント  
 これらのフラグに渡される、 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)と[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)メソッドのどのフィールドを示すために、 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造が初期化するのには。  
  
 使用、`dwFields`のメンバー、`DEBUG_REFERENCE_INFO`を示すためにどのフィールドに使用されると有効な構造が返される構造体。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)