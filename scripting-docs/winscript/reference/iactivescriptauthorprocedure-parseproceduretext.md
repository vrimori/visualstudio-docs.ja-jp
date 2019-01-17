---
title: IActiveScriptAuthorProcedure::ParseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 893dc36c066426ad1de7346c7ce1fea24b191ba3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090689"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
コード プロシージャを解析し、エンジンを作成するスクリプトにコード プロシージャのテキストを追加し、作成、`IScriptEntry`コード プロシージャに対応するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]項目の名前を含むバッファーのアドレスに関連付けられている、`IScriptEntry`オブジェクト。  
  
 `pszDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常 (など、2 つ単一引用符)、区切り記号を使用して、スクリプト ブロックの終了を検出します。 スクリプト ブロックの終わりをマークする区切り記号がない場合は、このパラメーターを NULL に設定します。  
  
 `dwCookie`  
 [in]アプリケーション定義の値に関連付けられた新しい`IScriptEntry`オブジェクト。  
  
 `dwFlags`  
 [in]使用されません。  
  
 `pdispFor`  
 [in]使用されません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 現在[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンがこのメソッドを実装していません。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthorProcedure インターフェイス](../../winscript/reference/iactivescriptauthorprocedure-interface.md)