---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
変数の値を受け取り、指定された型の新しいバリアントを作成します。  
  
## 構文  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### パラメーター  
 `pvarDst`  
 \[入力、出力\] `pvarSrc`で、`vtNew`で指定した型で表されるが値を格納するバリアント。  
  
 `pvarSrc`  
 \[入力\]新しい型に変更する、変数の値。  
  
 `lcid`  
 \[入力\]引数を文字列との間で変換するときに使用するロケールのコンテキスト。  
  
 `vtNew`  
 \[入力\] `pvarDst` があることができるように型を指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `pvarDst` と `pvarSrc` の引数は、初期値が上書きされると等しい場合があります。  このメソッドは `VariantClear` の関数に `pvarDst` を渡し、そのため `pvarDst` は有効な値に初期化する必要があります。  
  
## 参照  
 [IVariantChangeType インターフェイス](../../winscript/reference/ivariantchangetype-interface.md)