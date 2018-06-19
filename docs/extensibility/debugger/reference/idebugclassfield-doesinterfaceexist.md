---
title: IDebugClassField::DoesInterfaceExist |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7c4a09af356951e7e26b6c9b6b0af5922b9f53b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104177"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
特定のインターフェイスが、クラスで定義されているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszInterfaceName`  
 [in]検索するインターフェイス名を含む文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します、S_FALSE を返す場合は、インターフェイスが存在しません。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 有効で、このメソッドは、すべてのインターフェイスの列挙体を取得し、一致するインターフェイスのリストを検索します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)