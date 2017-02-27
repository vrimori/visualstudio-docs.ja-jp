---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

C \+\+. AMP アクセラレータのスタブ関数に対応するすべてのアクセラレータのポインターのタグの値を返します。  
  
## 構文  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### パラメーター  
 `cnt`  
 \[出力 `pPointerTags`入力\] 配列のサイズ。  
  
 `pcnt`  
 \[出力\] C\+\+ AMP アクセラレータのスタブ関数のアクセラレータのポインターのタグの数。  
  
 `pPointerTags`  
 \[入力\] アクセラレータのポインターのタグを格納 `DWORD` A の配列のポインターは C\+\+ AMP アクセラレータのスタブ関数で評価されます。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 解説  
 このメソッドは、. C\+\+ AMP アクセラレータのスタブ関数に対応する `IDiaSymbol` のインターフェイスで呼び出されます。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)