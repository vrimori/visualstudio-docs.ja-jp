---
title: "IDebugModule3::LoadSymbols |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
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
ms.openlocfilehash: 00b357a7c122de2788875632b770c4346963d975
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
現在のモジュールのシンボルを読み込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功したかどうか、それを返します`S_OK`です。 失敗した場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、現在の検索パスからシンボルを読み込みます (を呼び出して変更することができますが、 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)メソッド)。  
  
 このメソッドは、優先、 [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
