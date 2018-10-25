---
title: '1500: ca 変数名はないとフィールド名 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fdac60aa7b3fb37f45cff7c1c9e5f17920efed18
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173941"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: 変数名はフィールド名と同一にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [CA1500: 変数名は、フィールド名と一致する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names)docs.microsoft.com でリリースされました。  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|カテゴリ|Microsoft.Maintainability|  
|互換性に影響する変更点|フィールドと同じ名前を持つパラメーターで発生した: 場合<br /><br /> -改行なしの場合は、変更に関係なく、アセンブリ外フィールドとパラメーターを宣言するメソッドの両方を表示できません。<br />-重大 - フィールドの名前を変更し、アセンブリ外見なすことができます。<br />-重大な - パラメーターの名前を変更すると、アセンブリの外側に宣言するメソッドを確認できます。<br /><br /> フィールドと同じ名前を持つローカル変数で発生した: 場合<br /><br /> -改行なしで行った変更に関係なく、アセンブリの外部、フィールドを表示できない場合。<br />-改行なしの場合は、ローカル変数の名前を変更し、フィールドの名前は変更されません。<br />-重大な - フィールドの名前を変更すると、アセンブリの外側に表示されることができます。|  
  
## <a name="cause"></a>原因  
 インスタンス メソッドでは、パラメーターまたは宣言型のインスタンス フィールドと一致する名前を持つローカル変数を宣言します。 ルールに違反しているローカル変数をキャッチするには、デバッグ情報を使用してテスト対象のアセンブリをビルドし、関連付けられているプログラム データベース (.pdb) ファイルは、使用可能なである必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 インスタンス フィールドを使用してアクセスするインスタンス フィールドの名前には、パラメーターまたはローカル変数の名前が一致すると、 `this` (`Me`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) メソッドの本文のキーワード。 コードを保守する際に、簡単に、この違いを忘れるし、パラメーターまたはローカル変数がエラーにつながるインスタンス フィールドを指すことを前提としています。 これは時間のかかるメソッド本体に特に当てはまります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するのには、パラメーター/変数またはフィールドのいずれかの名前を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、ルールの 2 つの違反を示します。  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

