---
title: CONSTRUCTOR_ENUM |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 199201037889dbcb1b3019ef7632fc81e9c88db4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958658"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
さまざまな種類のコンス トラクターを選択します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>メンバー  
 crAll  
 すべてのコンス トラクターを選択します。  
  
 crNonStatic  
 非静的コンス トラクターを選択します。  
  
 crStatic  
 静的コンス トラクターを選択します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)