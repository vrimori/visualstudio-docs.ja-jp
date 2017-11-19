---
title: "IDebugProperty2::SetValueAsString |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsString
helpviewer_keywords: IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4046bfccac12e79992805e7abec7dfda65b5a658
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
指定した文字列からのプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszValue`  
 [in]設定する値を含む文字列。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するときに使用する基数。 基数を自動的に決定するしようとする場合は 0 を指定できます。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大の時間を指定します。 使用して`INFINITE`無制限に待機します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。 次の表は、他の値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|文字列をプロパティの値に変換できませんでしたまたはプロパティの値を設定できませんでした。|  
|`E_SETVALUE_VALUE_IS_READONLY`|プロパティは読み取り専用です。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)