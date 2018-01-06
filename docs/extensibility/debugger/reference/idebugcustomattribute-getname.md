---
title: "IDebugCustomAttribute::GetName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8237fe3ad25baa912ee3a1eb84da533d788346cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
カスタム属性の名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bstrName`  
 [out]カスタム属性の名前を表す文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって返される名前付き属性の宣言に使用するクラスの名前に対応します。 これは、可能性があります正確に一致しない名に対応するカスタム属性クラス自体の c# では"Attribute"サフィックスとして、宣言で使用されているときに、カスタム属性名から削除するとします。  
  
## <a name="see-also"></a>参照  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)