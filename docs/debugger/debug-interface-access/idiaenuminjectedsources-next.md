---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaEnumInjectedSources::Next メソッド"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンス内の挿入されたソースの指定した数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[出力\] 取得された列挙子の挿入されたソースの数。  
  
 rgelt  
 \[入力\] 目的の挿入されたソースを表す [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) のオブジェクトの配列を返します。  
  
 pceltFetched  
 \[入力\] 列挙子のフェッチ挿入されたソースの数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` これ以降挿入されたソースがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)