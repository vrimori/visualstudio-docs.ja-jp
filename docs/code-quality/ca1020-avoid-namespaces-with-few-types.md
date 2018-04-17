---
title: ': Ca 1020 名前空間のいくつかの種類 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a90f43735092591ad019fd2a46569e9302cf0c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: 型をほとんど含まない名前空間を使用しません
|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 グローバル名前空間以外の名前空間には、5 台未満の型が含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 論理構造を持つ各名前空間を付けます名前空間の型を配置する正当な理由が存在することを確認します。 名前空間には、ほとんどのシナリオで一緒に使用される型を含める必要があります。 各自のアプリケーションが相互に排他的な場合は、型にあるはず個別の名前空間。 たとえば、<xref:System.Web.UI>名前空間には、Web アプリケーションで使用される型が含まれています。 および<xref:System.Windows.Forms>名前空間には、で使用される型が含まれています。 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-ベースのアプリケーションです。 両方の名前空間では、ユーザー インターフェイスの側面を制御する型がある、でも、これらの型では、同じアプリケーションで使用する設計されていません。 そのため、ファイルは別の名前空間に配置します。 名前空間を慎重組織も役に立ちます機能の探索可能性を向上するため。 名前空間階層構造を確認するには、ライブラリのコンシューマーは、機能を実装する型を特定することにする必要があります。  
  
> [!NOTE]
>  デザイン時の型とアクセス許可をこのガイドラインに準拠するその他の名前空間にマージされません必要があります。 これらの型が、メインの名前空間の下に独自の名前空間に属しているし、名前空間の末尾には`.Design`と`.Permissions`、それぞれします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するのには、単一の名前空間に、一部の種類を含む名前空間を結合する再試行してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 名前空間には、他の名前空間内の型で使用される型が含まれていない場合、この規則による警告を抑制しても安全です。