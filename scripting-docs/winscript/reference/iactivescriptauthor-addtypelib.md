---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
スクリプトの名前空間にタイプ ライブラリを追加します。  
  
## 構文  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### パラメーター  
 `rguidTypeLib`  
 \[入力\]追加するタイプ ライブラリのクラス ID \(CLSID\)。  
  
 `dwMajor`  
 \[入力\]メジャー バージョン番号。  
  
 `dwMinor`  
 \[入力\]マイナー バージョン番号。  
  
 `dwFlags`  
 \[入力\] 使われません。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、タイプ ライブラリを読み込むために `LoadTypeLib` を呼び出します。  成功に、このメソッドは、型の情報を追加する `IActiveScriptAuthor::AddNamedItem` を呼び出します。  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/ja-jp/155b48e5-5438-409e-9342-630a6a500f60)