---
title: "SccGetVersion 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion 関数"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetVersion 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理プラグインでサポートされているソース管理プラグインの API のバージョン番号を取得します。  
  
## 構文  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### パラメーター  
 なし。  
  
## 戻り値  
 A `LONG` をサポートされているソース管理プラグインの API のバージョン番号を含むデータ型。  
  
|WORD|説明|  
|----------|--------|  
|HIWORD|メジャー バージョン|  
|LOWORD|マイナー バージョン|  
  
## 解説  
 たとえば、ソース管理プラグインでは、ソース管理プラグインの API のバージョン 1.3 をサポートする場合、この関数は 0x0103 に返します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)