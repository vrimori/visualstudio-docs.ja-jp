---
title: 'CA1725: パラメーター名は基本宣言を一致する必要があります |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d269d1f7bf373c9a0faedfe0f70b5192771fc4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: パラメーター名は基本宣言と同一でなければなりません
|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 外部から参照できるメソッド オーバーライドでパラメーターの名前が、基本メソッドの宣言、またはメソッドのインターフェイス宣言のパラメーターの名前のパラメーターの名前と一致しません。  
  
## <a name="rule-description"></a>規則の説明  
 オーバーライド階層のパラメーターに対する一貫性のある名前付けによって、メソッド オーバーライドの有用性が高まります。 派生メソッドのパラメーター名が基本宣言のパラメーター名と異なる場合、メソッドが基本メソッドのオーバーライドであるか、またはメソッドの新しいオーバーライドであるかについて混乱が生じる可能性があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、基本宣言と一致するパラメーターの名前を変更します。 修正プログラムは、COM 参照可能なメソッドの互換性に影響する変更です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 COM 参照可能なメソッドが以前に出荷されたライブラリ内を除き、この規則による警告は抑制しないでください。