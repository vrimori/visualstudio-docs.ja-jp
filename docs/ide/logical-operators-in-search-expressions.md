---
title: "検索式の論理演算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ヘルプ ビューアー 2.0、論理演算子 (検索での)"
  - "論理演算子 (検索での) [ヘルプ ビューアー 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 検索式の論理演算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

論理演算子を使用すると、簡単な検索式からより複雑な検索式を作成することによって、コンテンツの検索を絞り込むことができます。  次の表に示すように、論理演算子は、複数の検索用語を検索クエリでどのように組み合わせる必要があるかを指定します。  
  
> [!IMPORTANT]
>  検索エンジンが認識できるように、論理演算子をすべて大文字で入力する必要があります。  
  
|検索内容|使用|例|結果|  
|----------|--------|-------|--------|  
|同じトピック内の両方の用語|AND|dib AND palette|「dib」と「palette」の両方を含むトピック。|  
|トピック内のいずれかの用語|OR|raster OR vector|「raster」または「vector」を含むトピック。|  
|同じトピック内の最初の用語 \(2 番目の用語を含まない\)|NOT|"operating system" NOT DOS|「operating system」を含むが、「DOS」を含まないトピック。|  
|トピック内で近接する両方の用語|NEAR|user NEAR kernel|「kernel」にきわめて近い「user」を含むトピック。|  
  
## 参照  
 [フルテキスト検索のヒント](../ide/full-text-search-tips.md)   
 [情報の検索](../ide/locate-information.md)