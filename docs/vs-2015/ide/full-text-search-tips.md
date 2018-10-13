---
title: フルテキスト検索のヒント | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e05c7aa16d689dd037546fe9a199f43a80b0401
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303434"
---
# <a name="full-text-search-tips"></a>フルテキスト検索のヒント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ヘルプで情報を見つける簡単な方法の 1 つが、フルテキスト検索を実行することです。 結果を絞り込んだり、カスタマイズしたりするには、構文がクエリに与える効果を理解する必要があります。 このトピックでは、ヒント、手順、構文の詳細をご覧いただけます。効果的なクエリを作成できるようになります。  
  
## <a name="full-text-search-tips"></a>フルテキスト検索のヒント  
 クエリで使用した形式がヘルプでどのように解釈されるか理解していれば、自分が興味のあるトピックだけを返すようにターゲットを絞り込んだ検索クエリを作成できます。 形式には、特殊文字、予約語、フィルターがあります。  
  
### <a name="general-guidelines"></a>一般的なガイドライン  
 次の表は、ヘルプで検索クエリを作成するための基本的なルールとガイドラインをいくつか紹介したものです。  
  
|構文|説明|  
|------------|-----------------|  
|大文字と小文字の区別|検索では、大文字と小文字が区別されません。 大文字または小文字を使って検索条件を作成します。 たとえば、"OLE" と "ole" は同じ結果を返します。|  
|文字の組み合わせ|単一文字 (a–z) や単一数字 (0–9) だけを検索することはできません。 ”and”、”from”、”with” のような特定の予約語を検索しようとしても無視されます。 詳細については、このトピックの後半に登場する "検索で無視される言葉 (ストップ ワード)" をご覧ください。|  
|評価順序|検索クエリは左から右に評価されます。|  
  
### <a name="search-syntax"></a>検索構文  
 "word1 word2" のような複数の文字を含む検索文字列を指定した場合、その文字列は "word1 AND word2" を入力した場合と同じになり、検索文字列のすべての単語を含むトピックのみを返します。  
  
> [!IMPORTANT]
>  1.  句を検索することはできません。 検索文字列に複数の単語を指定した場合、返されるトピックには、指定したすべての単語が含まれますが、必ずしも指定した句とは厳密に同じにはなりません。  
> 2.  検索句の単語間の関係を指定するには、論理演算子を使用します。 AND、OR、NOT、NEAR のような論理演算子を追加し、検索をさらに絞り込むことができます。 たとえば、"declaring NEAR union" と検索すると、"declaring" という単語と "union" という単語がそれほど離れていないトピックが検索されます。 詳細については、「[検索式の論理演算子](../ide/logical-operators-in-search-expressions.md)」を参照してください。  
  
### <a name="filters"></a>フィルター  
 高度な検索演算子を利用し、検索結果をさらに制限できます。 ヘルプには、フルテキスト検索の結果を絞り込むためのカテゴリが 3 つあります。タイトル、コード、キーワードです。 詳細については、「[検索式の高度な検索演算子](../ide/advanced-search-operators-in-search-expressions.md)」を参照してください。  
  
### <a name="ranking-of-search-results"></a>検索結果のランク  
 検索アルゴリズムは特定の条件を適用し、結果一覧で検索結果を上または下のランクにします。 一般的には、次のようなランク付けが行われます。  
  
1.  タイトルに検索語を含むコンテンツは、それを含まないコンテンツより上のランクになります。  
  
2.  検索語が近接しているコンテンツは、そうではないコンテンツより上のランクになります。  
  
3.  検索語の密度が高いコンテンツは、密度が低いコンテンツより上のランクになります。  
  
### <a name="words-ignored-in-searches-stop-words"></a>検索で無視される言葉 (ストップ ワード)  
 よく使われる言葉や数字 (ストップ ワードと呼ばれることもあります) は、フルテキスト検索で自動的に無視されます。 たとえば、"pass through" という句を検索すると、"pass" という単語を含むトピックが表示され、"through" は無視されます。  
  
## <a name="see-also"></a>関連項目  
 [情報の検索](../ide/locate-information.md)   
 [検索式の論理演算子](../ide/logical-operators-in-search-expressions.md)



