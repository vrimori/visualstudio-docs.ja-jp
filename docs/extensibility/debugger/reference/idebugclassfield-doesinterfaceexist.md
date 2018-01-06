---
title: "IDebugClassField::DoesInterfaceExist |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::DoesInterfaceExist
helpviewer_keywords: IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d0e4535417f80198f06cb6b4255fea209b701e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)