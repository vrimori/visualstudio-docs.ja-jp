---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
バリアントをラップするプロパティ ブラウザーを返します。  
  
## 構文  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
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
  
 `ppdob`  
 \[入力\]プロパティ ブラウザー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドはバリアントをラップするプロパティ ブラウザーを返します。  
  
## 参照  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)