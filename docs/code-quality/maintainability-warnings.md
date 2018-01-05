---
title: "保守性に関する警告 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8d432dab79d5cd88d398a74c352cc9d34c8b4f2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="maintainability-warnings"></a>保守性に関する警告
保守性に関する警告は、ライブラリとアプリケーションの保守をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1500: 変数名はフィールド名と同一にすることはできません](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|インスタンス メソッドでは、パラメーターまたは名前には、エラーを宣言する型のインスタンス フィールドが一致するローカル変数を宣言します。|  
|[CA1501: 継承を使用しすぎないでください](../code-quality/ca1501-avoid-excessive-inheritance.md)|型が、その継承階層内の 5 つ以上深いレベルにあります。 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。|  
|[CA1502: メソッドの実装を複雑にしすぎないでください](../code-quality/ca1502-avoid-excessive-complexity.md)|この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。|  
|[CA1504: 紛らわしいフィールド名をレビューします](../code-quality/ca1504-review-misleading-field-names.md)|インスタンス フィールドの名前が「s _」、または静的な名前で始まる (内の共有[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) フィールドが「m _」で開始します。|  
|[CA1505: メンテナンスできないコードを使用しないでください](../code-quality/ca1505-avoid-unmaintainable-code.md)|型またはメソッドの保守容易性指数が低い値です。 保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。|  
|[CA1506: クラス結合度を大きくしすぎないでください](../code-quality/ca1506-avoid-excessive-class-coupling.md)|この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。|  
  
## <a name="see-also"></a>参照  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)