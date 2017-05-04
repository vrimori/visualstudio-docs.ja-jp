---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty メソッド, IActiveScriptProperty インターフェイス"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
パラメーターで指定されるプロパティを設定します。  
  
## 構文  
  
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
  
#### パラメーター  
 `dwProperty`  
 設定するプロパティ値。  
  
 `pvarIndex`  
 使用しません。  
  
 `pvarValue`  
 プロパティの値。  
  
 `dwProperty` に対して許可される値は、次の表に示します。  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|スクリプト エンジンを浮動小数点のモードではなく整数のモードで分割されます。  既定値 `False` です。|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|文字列を比較します。元のスクリプト エンジンの関数を許可します。|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|他のスクリプト エンジンがグローバル オブジェクトに関与するスクリプト エンジンにないことを通知します。|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンをサポートする一連の言語機能を選択するように強制します。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンによってサポートされている言語機能の既定のセットに設定 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンのバージョン 5.7 で表示される言語機能と同じです。|  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
  
## 解説  
 整数の除算を有効または無効にするには、`SetProperty` を起動し、`Object`に `Boolean` に変換します。  既定では、プロパティ値は `False`です。  セット `True`の除算演算をさらに整数だけを返します。  
  
 有効にするか、またはカスタム文字列比較を無効にし、`SetProperty` を起動し、`Object` の値を渡します。  に渡す [IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md)オブジェクトは、インターフェイスを実装する必要があります。  [IActiveScriptStringCompare インターフェイス](../../winscript/reference/iactivescriptstringcompare-interface.md) のインターフェイス [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) のメソッドは、文字列が関数を実行する比較するたびに呼び出されます。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンが初期化された時点でサポートする言語機能セットを選択するには、`SetProperty` を起動し、SCRIPTPROP\_INVOKEVERSIONING に対して有効にする言語機能のセットに対応する値を渡します。  このプロパティが 1 \(SCRIPTLANGUAGEVERSION\_5\_7\) に設定されている場合、使用できる言語機能は [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンのバージョン 5.7 では、同じです。  が 2 \(SCRIPTLANGUAGEVERSION\_5\_8\) に設定されている場合、使用できる言語機能は、バージョン 5.8 で追加された新機能とバージョン 5.7 に表示されていた機能です。  既定では、このプロパティは、ホストが別の既定の動作をサポートしていない場合、バージョン 5.7 で表示される言語機能と同じである 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\) を設定します。  たとえば、Internet Explorer 8 では、バージョン 5.8 の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンによって、既定ではサポート [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の言語機能と Internet Explorer 8 の既定のドキュメント モードが「Internet Explorer 8」の標準モードのときに選択します。  Internet Explorer 7 規格やひねりモードに Internet Explorer 8 のドキュメント モードを切り替えることによって、バージョン 5.7 の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンにある言語機能だけをサポートするために [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンをリセットします。  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING は [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンが初期化される場合にのみ設定してください。  
  
## 使用例  
 次の例では、整数の除算を使用する場合は、スクリプト エンジンを強制する方法、および比較関数のオーバーロードを使用する方法を示します。  
  
```csharp  
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
  
## 参照  
 [ドキュメントの互換性の定義](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)