---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
エラーを発生させたアプリケーションまたはクラスの言語に依存したプログラム ID を返します。  
  
## 構文  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### パラメーター  
 `pbstrSource`  
 \[入力\] `progname.objectname`フォームでプログラム ID を含む文字列です。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドで例外が発生したクラスまたはアプリケーションを決定するために使用されます。  プログラム ID は、呼び出しの時点に渡されるロケール識別子 \(LCID\) で指定された言語で返されることがあります。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## 参照  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)