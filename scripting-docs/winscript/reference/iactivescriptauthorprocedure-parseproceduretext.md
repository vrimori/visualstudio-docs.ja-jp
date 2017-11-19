---
title: "IActiveScriptAuthorProcedure::ParseProcedureText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
コードのプロシージャを解析し、エンジンを作成するスクリプトに、コードのプロシージャのテキストを追加し、作成、`IScriptEntry`コード プロシージャに対応するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [in]スクリプトのテキストを解析します。  
  
 `pszFormalParams`  
 [in]プロシージャの仮パラメーター名のアドレス。 パラメーター名は、エンジンを作成するスクリプトの適切な区切り記号で区切る必要があります。 名前は、かっこで囲まれていない必要があります。  
  
 `pszProcedureName`  
 [in]解析するプロシージャ名のアドレス。  
  
 `pszItemName`  
 [in]項目名を格納するバッファーのアドレスに関連付けられている、`IScriptEntry`オブジェクト。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常区切り文字を使用 (など、2 つ単一引用符)、スクリプト ブロックの終わりを検出します。 スクリプト ブロックの末尾を示すための区切り記号がない場合は、このパラメーターを NULL に設定します。  
  
 `dwCookie`  
 [in]新しいに関連付けられているアプリケーション定義の値`IScriptEntry`オブジェクト。  
  
 `dwFlags`  
 [in]使用しません。  
  
 `pdispFor`  
 [in]使用しません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 現在[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンがこのメソッドを実装していません。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthorProcedure インターフェイス](../../winscript/reference/iactivescriptauthorprocedure-interface.md)