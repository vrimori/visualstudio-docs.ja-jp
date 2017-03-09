---
title: "型 &#39;Object&#39; の引数を使う場合は、&#39;FilePut&#39; ではなく &#39;FilePutObject&#39; を使用してください。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrUseFilePutObject"
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;Object&#39; の引数を使う場合は、&#39;FilePut&#39; ではなく &#39;FilePutObject&#39; を使用してください。
`FilePut` メソッドには、型 `Object` の引数が含まれています。 あいまいさを避けるため、`FilePut` の代わりに `FilePutObject` を使用する必要があります。  
  
### このエラーを解決するには  
  
-   `FilePut` を `FilePutObject` に置き換えます。  
  
-   `Object` 引数をより具体的な種類にキャストします。  
  
-   `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## 参照  
 [ビルド内にありません: FilePutObject 関数](http://msdn.microsoft.com/ja-jp/a0f52a1c-5ecc-4945-b18c-03147af61d6b)   
 [My.Computer.FileSystem Object](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)   
 [My.Computer.FileSystem.WriteAllBytes メソッド](http://msdn.microsoft.com/ja-jp/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)