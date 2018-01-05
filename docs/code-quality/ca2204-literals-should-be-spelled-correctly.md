---
title: "CA2204: リテラル正しく入力されなければなりません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: リテラルは正しく入力されていなければなりません
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 パラメーターまたはローカライズされた文字列とリテラル文字列が必要なプロパティをリテラル文字列が使用されるメソッドのパスには、Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上が含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 このルールは、パラメーターまたはいずれかのプロパティに値として渡されたリテラル文字列をチェックまたは true は、次の場合の詳細。  
  
-   <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。  
  
-   パラメーターまたはプロパティ名には、"Text"、「メッセージ」または「キャプション」が含まれています。  
  
-   Console.Write または Console.WriteLine メソッドに渡される文字列パラメーターの名前は"value"か"format"。  
  
 このルールは、複合語をトークン化の単語にリテラル文字列を解析し、各単語/トークンのスペルをチェックします。 解析のアルゴリズムについては、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)です。  
  
 既定では、スペル チェックの英語 (en) バージョンを使用します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。 ユーザー辞書を使用する方法については、次を参照してください。[する方法: コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。 正しく単語のスペルを減らすために必要な新しいソフトウェア ライブラリを習得するまで時間。  
  
## <a name="related-rules"></a>関連規則  
 [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)