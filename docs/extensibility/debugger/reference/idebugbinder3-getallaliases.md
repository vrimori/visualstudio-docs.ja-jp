---
title: IDebugBinder3::GetAllAliases |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6da1b26b41c80d0417da16f478ef3f6672edd12a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099396"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
このメソッドは、プログラムからエイリアスの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `uRequest`  
 [in]返すエイリアスの最大数 (に渡される配列の長さを指定`ppAliases`)。  
  
 `ppAliases`  
 [入力、出力].エイリアスをコピーする配列 (これが null 値の場合と`uRequest`が 0 の場合で返すことができるエイリアスの数が返されます`puFetched`)。  
  
 `puFetched`  
 [out]取得する別名の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)