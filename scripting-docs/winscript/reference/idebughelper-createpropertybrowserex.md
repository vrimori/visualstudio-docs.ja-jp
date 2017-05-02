---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
バリアントをラップし、文字列に変数の値または VARTYPE の型のカスタム変換を許可するプロパティ ブラウザーを返します。  
  
## 構文  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### パラメーター  
 `pvar`  
 \[入力\]参照するルートのバリアント。  
  
 `bstrName`  
 \[入力\]ルートを与える名前。  
  
 `pdat`  
 \[入力\]要求プロパティにまたはのいずれかを実行します。  このパラメーターが NULL の場合、配置することは実行されません。  
  
 `pdf`  
 \[入力\]オブジェクト。バリアントにカスタム書式設定を提供する。  
  
 `ppdob`  
 \[入力\]プロパティ ブラウザー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドはバリアントをラップし、文字列に変数の値または VARTYPE の型のカスタム変換を許可するプロパティ ブラウザーを返します。  
  
## 参照  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)