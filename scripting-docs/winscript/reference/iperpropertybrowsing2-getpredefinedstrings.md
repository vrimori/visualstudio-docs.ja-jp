---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
呼び出し元は、このプロパティの潜在的な値を表す文字列の配列をポインターのカウントのリスト ボックスを塗りつぶすことができます。  
  
## 構文  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### パラメーター  
 `dispid`  
 \[入力\]呼び出し元が文字列の一覧を要求するプロパティの識別子をディスパッチします。  
  
 `pCaStrings`  
 \[入力\]文字列のポインターのメソッドに割り当てられた配列の要素数とアドレスを含む呼び出し元が割り当てた、カウントが設定された配列の構造体へのポインター。  メソッドが失敗した場合、メモリは割り当てられず、構造体の内容は未定義です。  
  
 `pCaCookies`  
 \[入力\]ダブル ワードのメソッドに割り当てられた配列の要素数とアドレスを含む呼び出し元が割り当てた、カウントが設定された配列の構造体へのポインター。  メソッドが失敗した場合、メモリは割り当てられず、構造体の内容は未定義です。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IPerPropertyBrowsing2 インターフェイス](../../winscript/reference/iperpropertybrowsing2-interface-1.md)