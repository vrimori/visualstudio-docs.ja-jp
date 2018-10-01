---
title: BPERESI_FIELDS |Microsoft Docs
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
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8207271404811f3da3dd03782974abd9e67fb576
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535385"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[BPERESI_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bperesi-fields)します。  
  
ブレークポイントの失敗した解像度について取得する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 初期化/使用、 `bpResLocation` (ブレークポイント解像度の位置) フィールドの[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)構造体。  
  
 BPERESI_PROGRAM  
 初期化/使用、`pProgram`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_THREAD  
 初期化/使用、`pThread`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_MESSAGE  
 初期化/使用、`bstrMessage`のフィールド、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_TYPE  
 初期化/使用、 `dwType` (ブレークポイントの種類) フィールドの`BP_ERROR_RESOLUTION_INFO`構造体。  
  
 BPERESI_ALLFIELDS  
 すべてのフィールドの初期化/使用して、`BP_ERROR_RESOLUTION_INFO`構造体。  
  
## <a name="remarks"></a>Remarks  
 パラメーターとして渡される、 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)のどのフィールドを示すメソッド、 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)構造体が初期化されるは。  
  
 これらの値は、どのフィールドを示すためにも使用、`BP_ERROR_RESOLUTION_INFO`構造体が返されるときに構造体が使用し、無効です。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

