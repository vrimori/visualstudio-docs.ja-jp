---
title: BP_LOCATION_CODE_STRING |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee33cff1ba8ee6ce278a9bb11f8967d4dd377173
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925275"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
統合開発環境 (IDE) から、ユーザーは入力文字列に基づくコードのブレークポイントを設定するために使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>メンバー  
 `bstrContext`  
 通常は、コード内のブレークポイント、コール スタックで見られる同様のメソッドまたは関数名のコンテキスト。  
  
 `bstrCodeExpr`  
 この文字列は、ユーザーがコードのブレークポイントを記述する型です。  
  
## <a name="remarks"></a>Remarks  
 この構造体のメンバーである、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)構造体、共用体の一部として。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)