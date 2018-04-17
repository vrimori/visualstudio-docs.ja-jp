---
title: '1713: イベントはありませんは before または after プレフィックス |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3daa93429a59e0b6c3f03db0fc62dd7850df3be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: イベントは、before または after プレフィックスを含むことはできません
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 イベントの名前は、'Before' や 'After' を開始します。  
  
## <a name="rule-description"></a>規則の説明  
 イベント名は、イベントを発生させるアクションを記述する必要があります。 特定のシーケンスで発生する関連イベントに名前を付ける場合、現在時制または過去時制を使用して、アクション シーケンスの相対的な位置を示します。 たとえば、リソースを終了するときに発生するイベントのペアの名前に、ときに可能性がありますの名前を付ける '終了' および 'BeforeClose' および 'AfterClose' の代わりに ' Closed'、します。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 イベント名のプレフィックスを削除して、現在時制または過去時制動詞に使用する名前の変更を検討してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。