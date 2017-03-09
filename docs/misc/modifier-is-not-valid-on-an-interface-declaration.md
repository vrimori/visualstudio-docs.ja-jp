---
title: "&#39;&lt;modifier&gt;&#39; は、Interface 宣言では有効ではありません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30397"
  - "vbc30397"
helpviewer_keywords: 
  - "BC30397"
ms.assetid: 9143dc87-c396-4ff9-9987-0b460ee32b38
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modifier&gt;&#39; は、Interface 宣言では有効ではありません
`Interface` 宣言で無効な修飾子が使用されました。`Interface` 宣言で宣言される `Sub`、`Function`、または `Property` ステートメントに有効な修飾子は `Overloads` と `Default` キーワードのみです。`Public`、`Private`、`Friend`、`Protected`、`Shared`、`Static`、`Overrides`、`MustOverride`、`Overridable` などの他の修飾子は無効です。  
  
 **エラー ID:** BC30397  
  
### このエラーを解決するには  
  
-   修飾子を削除します。  
  
## 参照  
 [ビルド内にありません: インターフェイス定義](http://msdn.microsoft.com/ja-jp/7840a52c-9c38-42c4-adbc-e2c02e9dc204)