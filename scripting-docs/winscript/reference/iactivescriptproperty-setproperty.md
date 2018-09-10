---
title: IActiveScriptProperty::SetProperty |Microsoft Docs
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
ms.openlocfilehash: 186608bc56cf8b3649f5beeb1e3a301580ce44bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279285"
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
  
|定数|[値]|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|浮動小数点のポイント モードではなく整数モードで分割するスクリプト エンジンを強制します。 既定値は `False` です。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|置き換えられるスクリプト エンジンの文字列比較関数を使用します。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|グローバル オブジェクトに貢献するその他のスクリプト エンジンが存在するスクリプト エンジンに通知します。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|力、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンをサポートする言語機能のセットを選択します。 既定でサポートされる言語機能のセット、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンがバージョン 5.7 のされていた言語機能セットと同じですが、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が有効ではありません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="remarks"></a>Remarks  
 を有効にまたは整数の除算を無効にするには呼び出す`SetProperty`し、変換、`Boolean`を、`Object`します。 プロパティの値は、既定では、`False`します。 設定した場合`True`、除算演算で整数のみが返されます。  
  
 を有効にまたはカスタムの文字列比較を無効にするには呼び出す`SetProperty`で渡すと、`Object`値。 渡すオブジェクトは、インターフェイスを実装する必要があります[IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md)します。 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md)のメソッド、 [IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md)インターフェイスには、文字列比較関数が実行されるたびに、呼ばれます。  
  
 ときにサポートされる言語機能のセットを選択して、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンが初期化されて、呼び出し`SetProperty`SCRIPTPROP_INVOKEVERSIONING に対して有効にする設定を言語の機能に対応する値を渡すとします。 このプロパティが 1 (SCRIPTLANGUAGEVERSION_5_7) に設定されている場合、利用可能な言語機能は、のバージョン 5.7 に表示されていたものと同じ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。 2 (SCRIPTLANGUAGEVERSION_5_8) に設定されている場合、バージョン 5.7 バージョン 5.8 で追加された新機能だけでなくで登場するものは、利用可能な言語機能。 既定でこのプロパティは、ホストが別の既定の動作をサポートしていない限りバージョン 5.7 に含まれる言語機能セットと同じです (SCRIPTLANGUAGEVERSION_DEFAULT) を 0 に設定されます。 Internet Explorer 8 に opts など、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 バージョンでサポートされている言語機能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]既定で Internet Explorer 8 の既定のドキュメント モードは、「Internet Explorer 8 標準」モードとスクリプト エンジンです。 リセットする Internet Explorer 7 標準、Internet Explorer 8 ドキュメント モード、Quirks モードの切り替え、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]バージョン 5.7 で存在していた言語機能セットのみをサポートするためにスクリプト エンジン[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。  
  
> [!NOTE]
>  場合にのみ SCRIPTPROP_INVOKEVERSIONING を設定する必要があります、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンが初期化されます。  
  
## <a name="example"></a>例  
 次の例では、整数の除算を使用するスクリプト エンジンを強制する方法との比較関数のオーバー ロードを許可する方法を示します。  
  
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
 [ドキュメントの互換性の定義](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)