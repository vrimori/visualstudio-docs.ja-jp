---
title: "Ca 1824: アセンブリを NeutralResourcesLanguageAttribute にマーク |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: アセンブリを NeutralResourcesLanguageAttribute に設定します
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 アセンブリに含まれる、 **ResX**-リソースのベースがありません、<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>を適用します。  
  
## <a name="rule-description"></a>規則の説明  
 **NeutralResourcesLanguage**属性通知、 **ResourceManager**のアセンブリのニュートラル カルチャのリソースを表示するために使用された言語です。 ニュートラル リソース言語と同じカルチャのリソースを検索するとき、 **ResourceManager**メイン アセンブリに格納されているリソースを自動的に使用します。 これは、サテライト アセンブリが現在のスレッドの現在のユーザー インターフェイス カルチャを検索する代わりにします。 これにより、読み込んだ最初のリソースに対する検索のパフォーマンスが向上し、ワーキング セットを縮小できます。  
  
## <a name="fixing-violations"></a>違反の修正  
 この規則違反を修正するには、アセンブリに属性を追加し、ニュートラル カルチャのリソースの言語を指定します。  
  
## <a name="specifying-the-language"></a>言語を指定します。  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>ニュートラル カルチャのリソースの言語を指定するには  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**です。  
  
2.  左側のナビゲーション バーから選択**アプリケーション**、クリックして**アセンブリ情報**です。  
  
3.  **アセンブリ情報** ダイアログ ボックスから言語を選択、**ニュートラル言語**ドロップダウン リスト。  
  
4.  **[OK]**をクリックします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制することはできます。 ただし、起動時のパフォーマンスが低下する可能性があります。