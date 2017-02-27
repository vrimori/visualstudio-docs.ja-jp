---
title: "IDiaSectionContrib::get_relocationsCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_relocationsCrc メソッド"
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSectionContrib::get_relocationsCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

セクションの再配置の \(CRC\) 情報を巡回詳細チェックを取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_relocationsCrc (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] セクションの再配置の詳細に CRC を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)