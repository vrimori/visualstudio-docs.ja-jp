---
title: IActiveScriptAuthor::GetScriptTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57513e51248e26e39f95871e0dad329e8cc2f82c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094706"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
スクリプト ブロックのテキスト属性を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [size_is で (`cch`)]、スクリプト ブロックのテキスト。 この文字列は null 終端ではありません。  
  
 `cch`  
 [in]使用する、サイズ、`pszCode`と`pattr`パラメーター。  
  
 `pszDelimiter`  
 [in]終了-スクリプトの区切り記号のアドレス。 ときに`pszCode`解析は、テキストのストリームからホスト通常 (など、2 つ単一引用符)、区切り記号を使用してスクリプトレットの末尾を検出します。 スクリプト ブロックの末尾を識別する区切り記号がない場合は、このパラメーターを NULL に設定します。  
  
 `dwFlags`  
 [in]スクリプト ブロックのテキストの属性に関連付けられているフラグです。 次の値の組み合わせになります。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER 属性の識別子を特定し、SOURCETEXT_ATTR_MEMBERLOOKUP 属性を持つドット演算子を識別します。|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS 属性を持つ現在のオブジェクトを識別します。|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT 属性が文字列のコンテンツおよびコメントのテキストを特定します。|  
  
 `pattr`  
 [in, out size_is (`cch`)]、スクリプト ブロックのコードの色の情報。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)