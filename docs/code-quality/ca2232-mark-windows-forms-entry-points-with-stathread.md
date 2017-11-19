---
title: "Ca 2232: Windows フォームのエントリ ポイントを stathread に設定しますが |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6dadac882d5a1b6bf96e4cb0f713979ff566116f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows フォームのエントリ ポイントを STAThread に設定します
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 アセンブリが参照、<xref:System.Windows.Forms>名前空間、およびそのエントリ ポイントでマークされていない、<xref:System.STAThreadAttribute?displayProperty=fullName>属性。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.STAThreadAttribute>COM アプリケーションのモデルのスレッドがシングル スレッド アパートメントであることを示します。 この属性は、Windows フォームを使用するすべてのアプリケーションのエントリ ポイントに指定する必要があります。省略すると、Windows コンポーネントが正常に機能しないことがあります。 属性が存在しない場合、アプリケーションは、Windows フォームではサポートされていない、マルチ スレッド アパートメント モデルを使用します。  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]アプリケーション フレームワークを使用するプロジェクトは、マークする必要はありません、 **Main**メソッドを stathread に設定します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]コンパイラでは、自動的にします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには追加、<xref:System.STAThreadAttribute>属性のエントリ ポイントにします。 場合、<xref:System.MTAThreadAttribute?displayProperty=fullName>属性が、これを削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 対象の .NET Compact Framework の開発している場合は、この規則による警告を抑制するのには安全では、<xref:System.STAThreadAttribute>属性は不要であり、サポートされていません。  
  
## <a name="example"></a>例  
 次の例では、正しい使用法<xref:System.STAThreadAttribute>です。  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]