---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

対応するタグの値の場合、このメソッドは、指定した相対仮想アドレスの指定した親のアクセラレータのスタブの関数に含まれるシンボルの列挙体を返します。  
  
## 構文  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] `IDiaSymbol` 検索するアクセラレータのスタブの関数に対応します。  
  
 `tagValue`  
 \[入力\] ポインターのタグの値。  
  
 `rva`  
 \[入力\] 相対仮想アドレス。  
  
 `ppResult`  
 \[入力\] 結果で初期化される `IDiaEnumSymbols` のインターフェイス ポインターへのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 解説  
 アクセラレータのスタブの関数に対応する `IDiaSymbol` のインターフェイスのみ、このメソッドを呼び出します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)