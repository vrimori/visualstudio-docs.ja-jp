---
title: "コンストラクターは、&#39;&lt;typename&gt;&#39; を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; を間接的に参照しています | Microsoft Docs"
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
  - "bc31528"
  - "vbc31528"
helpviewer_keywords: 
  - "BC31528"
ms.assetid: 33459c3f-8615-492e-b6ae-531ed597999e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コンストラクターは、&#39;&lt;typename&gt;&#39; を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; を間接的に参照しています
コンストラクターは、'\<typename\>' を含むアセンブリ '\<assemblyname\>' を間接的に参照しています。 プロジェクトに \<filename\> へのファイル参照を追加してください。  
  
 クラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されていますが、アセンブリには、型を定義するアセンブリへのプロジェクト参照がありません。  
  
 **エラー ID:** BC31528  
  
### このエラーを解決するには  
  
-   プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。  
  
## 参照  
 [ビルド内にありません: 同じ名前を持つ複数の変数がある場合に参照を解決する](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)