---
title: "IActiveScriptAuthor::ParseScriptText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
スクリプト テキストを解析し、エンジンを作成するスクリプトに、テキストを追加し、作成、`IScriptEntry`スクリプト ブロックに対応するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [in]スクリプトのテキストを解析します。  
  
 `pszItemName`  
 [in]スクリプト ブロックに関連付けられている項目の名前を含むバッファーのアドレス。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常区切り文字を使用 (など、2 つ単一引用符)、スクリプト ブロックの終わりを検出します。 スクリプト ブロックの末尾を識別する区切り記号がない場合は、このパラメーターを NULL に設定します。  
  
 `dwCookie`  
 [in]新しいに関連付けられているアプリケーション定義の値`IScriptEntry`オブジェクト。  
  
 `dwFlags`  
 [in]使用しません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)