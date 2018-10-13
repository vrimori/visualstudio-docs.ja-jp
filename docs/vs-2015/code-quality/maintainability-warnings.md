---
title: 保守性に関する警告 |Microsoft Docs
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
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f709a7bb2d433ab86b5088349f1977a66c9a4c42
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238499"
---
# <a name="maintainability-warnings"></a>保守性に関する警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

保守容易性の警告は、ライブラリとアプリケーションの保守をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1500: 変数名はフィールド名と同一にすることはできません](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|インスタンス メソッドでは、パラメーターまたはエラーにつながる、宣言型のインスタンス フィールドと一致する名前を持つローカル変数を宣言します。|  
|[CA1501: 継承を使用しすぎないでください](../code-quality/ca1501-avoid-excessive-inheritance.md)|型が、その継承階層内の 5 つ以上深いレベルにあります。 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。|  
|[CA1502: メソッドの実装を複雑にしすぎないでください](../code-quality/ca1502-avoid-excessive-complexity.md)|この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。|  
|[CA1504: 紛らわしいフィールド名をレビューします](../code-quality/ca1504-review-misleading-field-names.md)|インスタンス フィールドの名前が「s _」、または静的な名前で始まります (内の共有[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) フィールドが「m _」で開始します。|  
|[CA1505: メンテナンスできないコードを使用しないでください](../code-quality/ca1505-avoid-unmaintainable-code.md)|型またはメソッドの保守容易性指数が低い値です。 保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。|  
|[CA1506: クラス結合度を大きくしすぎないでください](../code-quality/ca1506-avoid-excessive-class-coupling.md)|この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。|  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



