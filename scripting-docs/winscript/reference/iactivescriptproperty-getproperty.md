---
title: IActiveScriptProperty::GetProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726052"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
パラメーターで指定されているプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwProperty`  
 プロパティの値を取得します。  
  
 `pvarIndex`  
 使用しません。  
  
 `pvarValue`  
 プロパティの値。  
  
 値が許可されている`dwProperty`は次の表で説明します。  
  
|定数|値|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|フローティング ポイント モードではなく整数モードで分割するスクリプト エンジンを強制します。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|交換するスクリプト エンジンの文字列比較関数を許可します。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|グローバル オブジェクトに影響を与える他のスクリプト エンジンが存在するスクリプト エンジンに通知します。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|強制的に実行、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンでサポートされる言語機能のセットを選択します。 既定でサポートされる言語機能のセット、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンがバージョン 5.7 のされていた言語機能セットと同じ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が有効ではありません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
  
## <a name="remarks"></a>コメント  
 ホストは、SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION プロパティを使用して、グローバル オブジェクトに影響を与える他のスクリプト エンジンが存在するスクリプト エンジンに通知することができます。 たとえば、Internet Explorer に通知できます、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]表示するページのみを含むエンジン[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト。 したがって、のみ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンは、グローバル オブジェクト ウィンドウに、新しいプロパティを追加することができ、同じ操作を実行する Visual Basic Scripting Edition (VBScript) エンジンはありません。 エンジンは、このフラグは無視してかまいませんまたはグローバル オブジェクトに追加される新しいメンバーの管理を最適化するために使用できます。  
  
 ホストは、SCRIPTPROP_INVOKEVERSIONING プロパティを使用する言語機能のセットを選択するときにサポートされている、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンが起動します。 利用可能な言語の機能のバージョン 5.7 に表示されていたものと同じではこのプロパティが 1 (SCRIPTLANGUAGEVERSION_5_7) に設定されている場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。 2 (SCRIPTLANGUAGEVERSION_5_8) に設定されている場合、利用可能な言語機能は、5.8 のバージョンで追加された機能だけでなくバージョン 5.7 に表示されていた。 既定は、バージョン 5.7 に表示されていた言語機能セット、ホストが別の既定の動作をサポートしていない限り 0 (SCRIPTLANGUAGEVERSION_DEFAULT) にこのプロパティが設定されます。 Internet Explorer 8 に opts のインスタンス、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 のバージョンでサポートされる言語機能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Internet Explorer 8 用のドキュメント モードが「Internet Explorer 8 標準」モードの場合、既定ではスクリプト エンジンです。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント互換性の定義](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)