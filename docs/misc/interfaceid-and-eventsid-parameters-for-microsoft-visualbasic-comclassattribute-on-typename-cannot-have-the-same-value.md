---
title: "&#39;&lt;typename&gt;&#39; では &#39;Microsoft.VisualBasic.ComClassAttribute&#39; の &#39;InterfaceId&#39; および &#39;EventsId&#39; パラメーターに同じ値を指定することはできません | Microsoft Docs"
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
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; では &#39;Microsoft.VisualBasic.ComClassAttribute&#39; の &#39;InterfaceId&#39; および &#39;EventsId&#39; パラメーターに同じ値を指定することはできません
`COMClassAttribute` 属性ブロックで、作成イベントと同じグローバル一意識別子 \(GUID\) がインターフェイスに指定されています。 これらの識別子を両方指定する場合は、これらを同じにすることはできません。 また、クラス識別子と同じにすることもできません。  
  
 GUID は、16 バイトで構成されます。前半の 8 バイトは数値、後半の 8 バイトはバイナリです。 uuidgen.exe などの Microsoft ユーティリティで生成され、一意であることが保証されています。  
  
 **エラー ID:** BC32507  
  
### このエラーを解決するには  
  
1.  COM オブジェクトのインターフェイスおよび作成イベントを識別するために必要な正しい GUID を確認します。  
  
2.  `COMClassAttribute` 属性ブロックに表示される GUID 文字列が正しくコピーされていることを確認します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)