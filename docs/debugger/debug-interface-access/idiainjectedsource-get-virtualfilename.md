---
title: "IDiaInjectedSource::get_virtualFilename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_virtualFilename メソッド"
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_virtualFilename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

非ファイルのソース・コードに割り当てられる名前を取得します ; つまり挿入されたコードにします。  
  
## 構文  
  
```cpp#  
HRESULT get_virtualFilename (   
   BSTR* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] 非ファイルの名前特定の挿入されたソース・コードを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)