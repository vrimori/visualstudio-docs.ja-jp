---
title: "SccBeginBatch 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch 関数"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccBeginBatch 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理操作のバッチ シーケンスを開始します。[SccEndBatch](../extensibility/sccendbatch-function.md) をバッチの終了が呼び出されます。 これらのバッチは、入れ子にできません。  
  
## 構文  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### パラメーター  
 なし。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|操作のバッチは正常に開始しました。|  
|SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
  
## 解説  
 ソース コントロールのバッチは、複数のプロジェクトまたは複数のコンテキスト全体にわたって同じ操作を実行に使用されます。 バッチ操作中に、ユーザー エクスペリエンスからプロジェクトごとの冗長なダイアログ ボックスを排除するバッチを使用できます。`SccBeginBatch` 関数と [SccEndBatch](../extensibility/sccendbatch-function.md) 関数のペアとして先頭と、操作の終了を示すために使用します。 入れ子にできません。`SccBeginBatch` バッチ操作が進行中であることを示すフラグを設定します。  
  
 バッチ操作の実行中に、ソース管理プラグインを多くて質問については、1 つのダイアログ ボックスをユーザーに提示し、すべての後続の演算でこのダイアログ ボックスからの応答を適用します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)