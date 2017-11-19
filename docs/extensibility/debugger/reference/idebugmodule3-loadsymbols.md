---
title: "IDebugModule3::LoadSymbols |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::LoadSymbols
helpviewer_keywords: IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88789800e0e93f07b953417214bde8852def32f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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