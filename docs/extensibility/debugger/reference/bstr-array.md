---
title: "BSTR_ARRAY |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 10
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0e1d2b2228085505971102494522cdf9085d4a67
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="bstrarray"></a>BSTR_ARRAY
文字列の配列を記述する構造。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>用語  
 dwCount  
 数値の文字列の`Members`配列。  
  
 メンバー  
 文字列の配列。  
  
## <a name="remarks"></a>コメント  
 この構造体から返される、 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)メソッドです。  
  
 [C++ のみ]使用して各個々 の文字列を解放する必要があります`SysFreeString`、および`Members`配列を使用して解放する必要があります`CoTaskMemFree`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
