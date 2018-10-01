---
title: 検索式の論理演算子 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535069"
---
# <a name="logical-operators-in-search-expressions"></a>検索式の論理演算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[検索式の論理演算子](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions)します。  
  
論理演算子を使用すると、より単純な検索式からより複雑な検索式を作成して、コンテンツの検索を絞り込むことができます。 次の表に示すように、論理演算子では、複数の検索用語を検索クエリでどのように組み合わせる必要があるかを指定します。  
  
> [!IMPORTANT]
>  検索エンジンが認識できるように、論理演算子をすべて大文字で入力する必要があります。  
  
|検索対象|使用|例|結果|  
|-------------------|---------|-------------|------------|  
|同じトピック内の両方の用語|AND|dib AND palette|"dib" と "palette" の両方を含むトピック。|  
|トピック内のいずれかの用語|OR|raster OR vector|"raster" または "vector" を含むトピック。|  
|同じトピック内の最初の用語 (2 番目の用語を含まない)|NOT|"operating system" NOT DOS|"operating system" を含むが、"DOS" を含まないトピック。|  
|トピック内で近接する両方の用語|NEAR|user NEAR kernel|"kernel" にきわめて近い "user" を含むトピック。|  
  
## <a name="see-also"></a>関連項目  
 [フルテキスト検索のヒント](../ide/full-text-search-tips.md)   
 [情報の検索](../ide/locate-information.md)



