---
title: IActiveScriptAuthor::GetScriptletTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0973b2943ed76a7baa231a287476b237cd45e257
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095460"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
スクリプトレットのテキスト属性を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [size_is で (`cch`)] スクリプトレット テキスト。 この文字列は null 終端ではありません。  
  
 `cch`  
 [in]使用する、サイズ、`pszCode`と`pattr`パラメーター。  
  
 `pszDelimiter`  
 [in]スクリプトレットの末尾の区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常 (など、2 つ単一引用符)、区切り記号を使用してスクリプトレットの末尾を検出します。 スクリプトレットの末尾を識別するために区切り記号を使用しない場合は、このパラメーターを NULL に設定します。  
  
 `dwFlags`  
 [in]スクリプトレットのテキストの属性に関連付けられているフラグです。 次の値の組み合わせを指定できます。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER 属性の識別子を特定し、SOURCETEXT_ATTR_MEMBERLOOKUP 属性を持つドット演算子を識別します。|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS 属性を持つ現在のオブジェクトを識別します。|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT 属性が文字列のコンテンツおよびコメントのテキストを特定します。|  
  
 `pattr`  
 [in, out size_is (`cch`)] スクリプトレット コードの色の情報。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)