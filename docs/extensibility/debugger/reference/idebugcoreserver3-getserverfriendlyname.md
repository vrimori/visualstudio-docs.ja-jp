---
title: IDebugCoreServer3::GetServerFriendlyName |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811292ff5f7dd95e127e63d30bf14ee06269ff7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107791"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
サーバーのフレンドリ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrName`  
 [out]サーバーのフレンドリ名を返します。  
  
> [!NOTE]
>  呼び出し元は、文字列を解放します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ユーザーが起動のサーバーでは、このメソッドによって返される名前は、サーバーの完全な名前です。 サーバーの自動起動の名前は、マシンのサーバーが実行されていることです。  
  
 コンピューター対象の名前では、呼び出し、 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)