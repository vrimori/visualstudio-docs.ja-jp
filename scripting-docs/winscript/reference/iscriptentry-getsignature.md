---
title: "IScriptEntry::GetSignature |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
タイプの情報を返す、`IScriptEntry`関数オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppti`  
 [out]これに関連付けられている情報を入力`IScriptEntry`関数オブジェクト。  
  
 `piMethod`  
 [out]内のメソッドのインデックス、`ITypeInfo`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 使用して型情報を設定する[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)または[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)です。 型情報は、関数の内部表現に基づくエントリによっても生成できます。  
  
## <a name="see-also"></a>関連項目  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)