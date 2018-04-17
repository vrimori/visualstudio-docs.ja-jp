---
title: 'Ca 2121: 静的コンス トラクターをプライベートにする必要があります |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6248371d4089b4d1e651a9ea3c391d293b94f40c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: 静的コンストラクターはプライベートでなければなりません
|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 型は、プライベートではない静的コンス トラクターを持ちます。  
  
## <a name="rule-description"></a>規則の説明  
 静的コンス トラクター、クラス コンス トラクターとも呼ばれますが、型の初期化に使用されます。 システムで静的コンストラクターが呼び出されてから、型の最初のインスタンスが作成されるか、静的メンバーが参照されます。 ユーザーには、静的コンス トラクターが呼び出されたときに制御がありません。 静的コンストラクターがプライベートである場合、システム以外のコードから呼び出すことができます。 コンストラクターで実行される操作によっては、これによって予期しない動作が発生することがあります。  
  
 このルールは、c# および Visual Basic コンパイラによって強制されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 違反は、通常、次のアクションのいずれかで発生します。  
  
-   型の静的コンス トラクターを定義しておかなかったにプライベートです。  
  
-   プログラミング言語のコンパイラでは、型に既定の静的コンス トラクターを追加し、おかなかったにプライベートです。  
  
 1 つ目の違反を修正するには、プライベート、静的コンス トラクターを確認します。 2 番目の種類を修正するには、型にプライベートな静的コンス トラクターを追加します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 これらの違反は抑制しないでください。 ソフトウェアの設計では、静的コンス トラクターを明示的に呼び出す必要がある場合、通常は、デザイン重大な欠陥が含まれていますなり見直す必要があります。