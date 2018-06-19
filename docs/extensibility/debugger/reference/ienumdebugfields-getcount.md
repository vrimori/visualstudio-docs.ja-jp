---
title: IEnumDebugFields::GetCount |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0143685e5e959b36c6d4bdcb9cc122fc7d7db10
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123225"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
このメソッドは、列挙体の要素の数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcelt`  
 [out]列挙体の要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、実装するのには、[次へ、複製、スキップ]、およびリセット必要がありますを指定する、一般的な列挙の COM インターフェイスの一部ではありません。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)