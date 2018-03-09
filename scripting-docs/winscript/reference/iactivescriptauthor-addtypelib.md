---
title: "IActiveScriptAuthor::AddTypeLib |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 150628f1822c721f1e349005de457951e226ef1b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
スクリプトの名前空間をタイプ ライブラリを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rguidTypeLib`  
 [in]\(クラス id) の CLSID、タイプ ライブラリを追加します。  
  
 `dwMajor`  
 [in]メジャー バージョン番号。  
  
 `dwMinor`  
 [in]マイナー バージョン番号。  
  
 `dwFlags`  
 [in]使用しません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出す`LoadTypeLib`タイプ ライブラリを読み込めません。 成功すると、このメソッドを呼び出す`IActiveScriptAuthor::AddNamedItem`型情報を追加します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/en-us/155b48e5-5438-409e-9342-630a6a500f60)