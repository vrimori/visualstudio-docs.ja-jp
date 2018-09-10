---
title: IActiveScriptAuthor::AddTypeLib |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1122b5327da5573071bc534b5eb1a16fa69b873
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283380"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
スクリプトの名前空間には、タイプ ライブラリを追加します。  
  
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
 [in]使用されません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出す`LoadTypeLib`タイプ ライブラリを読み込めません。 成功すると、このメソッドを呼び出す`IActiveScriptAuthor::AddNamedItem`型情報を追加します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)