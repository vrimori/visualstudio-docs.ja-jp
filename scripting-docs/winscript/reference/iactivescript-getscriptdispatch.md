---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
現在実行中のスクリプトに関連付けられているメソッドとプロパティの `IDispatch` のインターフェイスを取得します。  
  
## 構文  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### パラメーター  
 `pstrItemName`  
 \[入力\]呼び出し元が関連付けられたディスパッチ オブジェクトを必要とする項目の名前を含むバッファーのアドレス。  このパラメーターがの場合、ディスパッチ `NULL`オブジェクトはスクリプトで定義されているグローバル メソッドとプロパティのすべてのメンバーとして格納されます。  `IDispatch` のインターフェイスと `ITypeInfo` の関連インターフェイスを通じて、ホストはスクリプト メソッドまたはビューを起動し、スクリプトの変数を変更できます。  
  
 `ppdisp`  
 \[入力\]オブジェクトへのポインターを受け取る変数のアドレスはスクリプトのグローバル メソッドとプロパティに関連付けられています。  スクリプト エンジンがこのようなオブジェクトをサポートしていない場合、`NULL` が返されます。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
|`S_FALSE`|スクリプト エンジンはディスパッチ オブジェクトをサポートしていません; `ppdisp` のパラメーターが null 値に設定されます。|  
  
## 解説  
 メソッドとプロパティが [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) のインターフェイスを呼び出すことで追加できるため、返される `IDispatch` のインターフェイスは、このメソッドによって動的に新しいメソッドおよびプロパティをサポートできます。  同様に、`IDispatch::GetTypeInfo` のメソッドはメソッドとプロパティが追加されたときに `ITypeInfo` の新しい一意なインターフェイスを返す必要があります。  ただし、言語のエンジンが `ITypeInfo` の前のインターフェイスと互換性がない方法で `IDispatch` のインターフェイスを変更してはならない点に注意が返されました。  これは DISPID が、再利用されていないこと、たとえば意味します。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)