---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty メソッド, IActiveScriptProperty インターフェイス"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
パラメーターで指定されるプロパティを取得します。  
  
## 構文  
  
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
  
#### パラメーター  
 `dwProperty`  
 取得するプロパティ値。  
  
 `pvarIndex`  
 使用しません。  
  
 `pvarValue`  
 プロパティの値。  
  
 `dwProperty` に対して許可される値は、次の表に示します。  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|スクリプト エンジンを浮動小数点のモードではなく整数のモードで分割されます。|  
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
 ホストは、他のスクリプト エンジンがグローバル オブジェクトに関与することなく、スクリプト エンジンに通知 SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION のプロパティを使用できます。  たとえば、Internet Explorer が表示されるページが [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプトだけが含まれていること [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] エンジンを通知できます。  したがって、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] エンジンだけをグローバル オブジェクト ペインに新しいプロパティを追加できます。同じにする Visual Basic Scripting Edition \(VBScript\) エンジンはありません。  エンジンはこのフラグを無視するか、グローバルなオブジェクトに追加された新しいメンバーの管理を最適化するために使用できます。  
  
 ホストは [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンの起動時サポートする言語機能セットを選択するに SCRIPTPROP\_INVOKEVERSIONING のプロパティを使用できます。  このプロパティが 1 \(SCRIPTLANGUAGEVERSION\_5\_7\) に設定されている場合、使用できる言語機能は [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンのバージョン 5.7 では、同じです。  が 2 \(SCRIPTLANGUAGEVERSION\_5\_8\) に設定されている場合、使用できる言語機能は、バージョン 5.8 で追加された機能とバージョン 5.7 に表示されていた機能です。  既定では、このプロパティは、ホストが別の既定の動作をサポートしていない場合、バージョン 5.7 で表示される言語機能と同じである 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\) を設定します。  たとえば、Internet Explorer 8 では、バージョン 5.8 の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のスクリプト エンジンによって、既定ではサポート [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の言語機能と Internet Explorer 8 のドキュメント モードが「Internet Explorer 8」の標準モードのときに選択します。  
  
## 参照  
 [ドキュメントの互換性の定義](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)