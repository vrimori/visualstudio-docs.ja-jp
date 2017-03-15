---
title: "PARSEFLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04cf02cc21fd6ae7324267805e89b1454566b9b6
ms.lasthandoff: 02/22/2017

---
# <a name="parseflags"></a>PARSEFLAGS
式を解析する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```c#  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>メンバー  
 PARSE_EXPRESSION  
 式がステートメントではないことを示します。  
  
 PARSE_FUNCTION_AS_ADDRESS  
 式が解析 (と後で評価) アドレスとしてことを示します。  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 式がデザイン時に解析されていることを示します (つまり、デザイナーが開いているとき)。  
  
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
