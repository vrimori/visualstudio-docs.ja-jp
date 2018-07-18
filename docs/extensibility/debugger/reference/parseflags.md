---
title: PARSEFLAGS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70766aef19c199a191f141947f1b5a458450c322
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126192"
---
# <a name="parseflags"></a>PARSEFLAGS
式を解析する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>メンバー  
 PARSE_EXPRESSION  
 式がステートメントでないことを示します。  
  
 PARSE_FUNCTION_AS_ADDRESS  
 式が解析 (および後で評価) アドレスとしてのことを示します。  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 デザイン時に式が解析されていることを示します (つまり、デザイナーが開いているとき)。  
  
## <a name="remarks"></a>コメント  
 パラメーターとして渡される、 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)と[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)