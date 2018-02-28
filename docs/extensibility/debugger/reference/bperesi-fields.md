---
title: "BPERESI_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 36ac591940acaed2ac8b8f92c701580d9d45f94a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bperesifields"></a>BPERESI_FIELDS
ブレークポイントの失敗の解決策について取得する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 PERESI_BPRESLOCATION  
 初期化/を使用して、 `bpResLocation` (ブレークポイントの解像度の位置) フィールドの[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)構造体。  
  
 BPERESI_PROGRAM  
 初期化/を使用して、`pProgram`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_THREAD  
 初期化/を使用して、`pThread`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_MESSAGE  
 初期化/を使用して、`bstrMessage`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_TYPE  
 初期化/を使用して、 `dwType` (ブレークポイントの種類) フィールドの`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_ALLFIELDS  
 すべてのフィールドを使用して初期化、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
## <a name="remarks"></a>コメント  
 パラメーターとして渡される、 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)メソッドのどのフィールドを示すために、 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)構造が初期化するのには。  
  
 これらの値がでどのフィールドを示すためにも使用、`BP_ERROR_RESOLUTION_INFO`構造使用されていて有効な場合、その構造が返されます。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)