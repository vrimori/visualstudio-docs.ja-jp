---
title: IActiveScriptProperty::SetProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726502"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
パラメーターで指定されているプロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetProperty(  
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
 設定するプロパティ値。  
  
 `pvarIndex`  
 使用しません。  
  
 `pvarValue`  
 プロパティの値。  
  
 値が許可されている`dwProperty`は次の表で説明します。  
  
|定数|値|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|フローティング ポイント モードではなく整数モードで分割するスクリプト エンジンを強制します。 既定値は `False` です。|  
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
 有効にするにまたは整数の除算を無効にするには、呼び出す`SetProperty`し、変換、`Boolean`を`Object`です。 プロパティの値は、既定では、`False`です。 設定した場合`True`、除算演算で整数のみが返されます。  
  
 有効または無効にカスタムの文字列比較、呼び出す`SetProperty`を渡して、`Object`値。 渡されたオブジェクトは、インターフェイスを実装する必要があります[IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md)です。 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md)のメソッド、 [IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md)インターフェイスには、文字列比較関数が実行されるたびに、呼ばれます。  
  
 ときにサポートする言語機能のセットを選択する、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンが初期化されて、呼び出し`SetProperty`SCRIPTPROP_INVOKEVERSIONING に対して有効にする言語機能に対応する値を渡します。 利用可能な言語の機能のバージョン 5.7 に表示されていたものと同じではこのプロパティが 1 (SCRIPTLANGUAGEVERSION_5_7) に設定されている場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。 2 (SCRIPTLANGUAGEVERSION_5_8) に設定されている場合、利用可能な言語機能は、5.8 のバージョンで追加された新機能だけでなくバージョン 5.7 に表示されていた。 既定は、バージョン 5.7 に表示されていた言語機能セット、ホストが別の既定の動作をサポートしていない限り 0 (SCRIPTLANGUAGEVERSION_DEFAULT) にこのプロパティが設定されます。 Internet Explorer 8 に opts など、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 のバージョンでサポートされている言語機能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Internet Explorer 8 の既定のドキュメント モードが「Internet Explorer 8 標準」モードの場合、既定ではスクリプト エンジンです。 リセットする Internet Explorer 7 標準、Internet Explorer 8 ドキュメント モードまたは Quirks モードの切り替え、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]バージョン 5.7 に存在する言語機能のセットのみをサポートするスクリプト エンジン[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING を指定する場合にのみ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンを初期化しています。  
  
## <a name="example"></a>例  
 次の例では、整数の除算を使用するスクリプト エンジンを強制する方法と、比較関数のオーバー ロードを許可する方法を示します。  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント互換性の定義](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)