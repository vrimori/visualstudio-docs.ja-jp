---
title: IDebugModule3::LoadSymbols |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab00d1bf3743cf3785bcac5491655cf31c12bd39
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898253"
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
 返します、メソッドが成功したかどうかは`S_OK`します。 失敗した場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、現在の検索パスからシンボルを読み込みます (呼び出すことによって変更できますが、 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)メソッド)。  
  
 このメソッドより優先、 [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)