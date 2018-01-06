---
title: "IDebugDefaultPort2::QueryIsLocal |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords: IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d52ee13002cc53084bc4f81b8cb65d489f3932d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
このメソッドでは、このポートは、ローカル コンピューター上にあるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`のかどうか、ローカル (上の呼び出し元と同じコンピューター) はこのポートまたは`S_FALSE`ポートが別のコンピューター上にある場合。  
  
## <a name="see-also"></a>参照  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)