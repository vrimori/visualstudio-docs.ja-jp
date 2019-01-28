---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da6b3641a33a19cef01f9a6a4a9a833643169f25
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006568"
---
# <a name="parseflags"></a>PARSEFLAGS
式を解析する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>メンバー  
 PARSE_EXPRESSION  
 式がステートメントではないことを示します。  
  
 PARSE_FUNCTION_AS_ADDRESS  
 解析 (および後で評価) アドレスとして、式があることを示します。  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 式はデザイン時に解析されていることを示します (つまり、デザイナーが開いているとき)。  
  
## <a name="remarks"></a>Remarks  
 パラメーターとして渡される、 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)と[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)