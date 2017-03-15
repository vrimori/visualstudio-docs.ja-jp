---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

対応するタグの値の場合、このメソッドは、指定した相対仮想アドレスのスタブこの関数に含まれるシンボルの列挙体を返します。  
  
## 構文  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### パラメーター  
 `tagValue`  
 \[入力\] pointee のシンボルを記録するポインターのタグの値はです。  
  
 `rva`  
 \[出力\] 指定したタグの値と pointee の変数に対応するシンボルをフィルター処理に使用する rva。  
  
 `ppResult`  
 \[入力\] 結果で初期化される `IDiaEnumSymbols` のインターフェイス ポインターへのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 解説  
 アクセラレータのスタブの関数に対応する `IDiaSymbol` のインターフェイスのみ、このメソッドを呼び出します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)