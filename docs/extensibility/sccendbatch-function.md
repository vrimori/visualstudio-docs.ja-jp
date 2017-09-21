---
title: "SccEndBatch 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch 関数"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccEndBatch 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理操作のバッチを終了します。 これらのバッチは、入れ子にできません。  
  
## 構文  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### パラメーター  
 なし。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|操作のバッチは正常に終了しました。|  
|SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
  
## 解説  
 ソース コントロールのバッチは、複数のプロジェクトまたは複数のコンテキスト全体にわたって同じソース管理操作を実行に使用されます。 バッチ操作中に、ユーザー エクスペリエンスから冗長なダイアログ ボックスを排除するバッチを使用できます。[SccBeginBatch](../extensibility/sccbeginbatch-function.md) と `SccEndBatch` 関数として使用する 2 つを先頭と操作の終了を示します。 入れ子にできません。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)