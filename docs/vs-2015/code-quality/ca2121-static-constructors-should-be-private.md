---
title: 'Ca 2121: 静的コンス トラクターはプライベートでなければなりません。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b7052a25df5e736276b458247eb625ab584d473
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589601"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: 静的コンストラクターはプライベートでなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2121: 静的コンス トラクターはプライベートでなければなりません](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)します。

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型には、プライベートでない静的コンス トラクターがあります。

## <a name="rule-description"></a>規則の説明
 静的コンス トラクター、クラス コンス トラクターとも呼ばれますが、型の初期化に使用されます。 システムで静的コンストラクターが呼び出されてから、型の最初のインスタンスが作成されるか、静的メンバーが参照されます。 ユーザーには、静的コンス トラクターが呼び出されたときに制御がありません。 静的コンストラクターがプライベートである場合、システム以外のコードから呼び出すことができます。 コンストラクターで実行される操作によっては、これによって予期しない動作が発生することがあります。

 このルールは、c# および Visual Basic .NET コンパイラによって強制されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 違反は、通常、次の操作のいずれかで発生します。

-   型の静的コンス トラクターを定義し、でした、プライベートにしません。

-   プログラミング言語のコンパイラでは、型に既定の静的コンス トラクターを追加しを行わなかったことプライベートします。

 1 つ目の違反を修正するには、静的コンス トラクターをプライベートにします。 2 つ目の種類を解決するの型にプライベート静的コンス トラクターを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 これらの違反を抑制しないでください。 ソフトウェアの設計では、静的コンス トラクターを明示的に呼び出す必要がある場合は、設計が重大な欠陥が含まれていて、確認する必要がありますは高くなります。



