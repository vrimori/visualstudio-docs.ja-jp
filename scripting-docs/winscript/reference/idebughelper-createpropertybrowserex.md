---
title: "IDebugHelper::CreatePropertyBrowserEx |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
バリアント型をラップして、文字列へのバリアント型の値または VARTYPE 型のカスタム変換できるように、プロパティ ブラウザーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvar`  
 [in]参照するルート バリアント。  
  
 `bstrName`  
 [in]ルートを指定する名前。  
  
 `pdat`  
 [in]プロパティを要求するスレッドします。 このパラメーターが NULL の場合は、マーシャ リングは実行されません。  
  
 `pdf`  
 [in]バリアントのカスタム書式設定を提供するオブジェクト。  
  
 `ppdob`  
 [out]プロパティ ブラウザー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、バリアント型をラップして、文字列へのバリアント型の値または VARTYPE 型のカスタム変換できるように、プロパティ ブラウザーを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)