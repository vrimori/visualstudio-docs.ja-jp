---
title: IDebugEngine3::LoadSymbols |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fde88d8ecc31c9e1326b36da33c7fd96530ff86d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
このデバッグ エンジンでは、デバッグされているすべてのモジュールのシンボルを読み込みます (必要に応じて)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。エラー コードを返しますそれ以外の場合。  
  
## <a name="remarks"></a>コメント  
 これには、このデバッグ エンジンによって参照されるすべてのモジュールのデバッグ シンボルが読み込まれます。 既に読み込まれていない場合にのみ、シンボルが読み込まれます。 呼び出しによって設定パスにシンボルが検索[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)です。  
  
## <a name="see-also"></a>関連項目  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)