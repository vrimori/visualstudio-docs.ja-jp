---
title: FIELD_KIND_EX |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6954aaf92c5d77ad4d8f51e6b342bfc021b37a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870876"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
フィールドの追加の種類を列挙する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクトに含めることができます。 この列挙体を拡張、 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)列挙体。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```csharp  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## <a name="members"></a>メンバー  
 FIELD_KIND_EX_NONE  
 フィールドに、拡張の型が含まれていません。  
  
 FIELD_TYPE_EX_METHODVAR  
 フィールドには、メソッドの変数が含まれています。  
  
 FIELD_TYPE_EX_CLASSVAR  
 フィールドには、クラス変数が含まれています。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)