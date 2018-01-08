---
title: "フォントと色の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09597130864ae0c1e79ef7470c58b25dde8a9263
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="font-and-color-overview"></a>フォントと色の概要
このトピックのテキストのフォントと色の設定、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 カテゴリとアイテムの表示の概念も導入されています。 および、Vspackage とコア エディターのテキスト属性を使用する方法を示します。  
  
## <a name="the-fonts-and-colors-property-page"></a>フォントおよび色 プロパティ ページ  
 表示されるテキストの属性を管理することができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を通じて統合開発環境 (IDE)、**フォントおよび色**プロパティ ページ。 検索する、**フォントおよび色**プロパティ ページで 、**ツール** メニューのをクリックして**オプション**です。 展開**環境**、クリックして**フォントおよび色**です。  
  
## <a name="categories-and-display-items"></a>カテゴリとアイテムを表示  
 フォントおよび色は整理**カテゴリ**と**表示項目**です。  
  
-   A**カテゴリ**の数の論理または機能のコンテナーは、**表示項目**です。  
  
     一連の**カテゴリ**では、**設定の表示**のドロップダウン ボックス、**フォントおよび色**プロパティ ページ。  
  
-   A**表示項目**コメント、文字列、または表示されるときに色で表示されるコントロールの構造体などのテキストが適切に定義されたエンティティします。  
  
 各**表示項目**内で一意に定義されて、**カテゴリ**含まれています。 その結果、1 つ以上**カテゴリ**持つことができます、**表示項目**と同じ名前です。  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage のコントロールのフォントと色  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]に Vspackage を使用します。  
  
-   フォントと色を定義する**カテゴリ**です。  
  
-   フォントと色を表示するために指定**表示項目**です。  
  
-   対話、**フォントおよび色**プロパティ ページ。  
  
-   集計の複数**カテゴリ**をグループにします。  
  
-   既定の設定の変更を保持します。  
  
 内のフォントと色の選択範囲と対話する方法を次の 2 つが、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]です。  
  
-   1 つの方法と呼びます*構文の色分け*です。 既存のカスタマイズ、VSPackage によって使用されている[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]言語サービスを実装し、ソース エディターを作成するためのエディターです。  
  
     1 つだけ**カテゴリ**つまりこのメカニズムをサポートしている場合、**テキスト エディター**です。  
  
-   他のすべての一般的な代替手段をサポートしている**カテゴリ**とテキストを表示するときに、ソース エディター以外のユーザー インターフェイス コンポーネント。 詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>」を参照してください。  
  
## <a name="core-editor-text-settings"></a>コア エディターのテキストの設定  
 言語サービス オブジェクトのコア エディターのフォントと色の設定が管理して、**テキスト EditorCategory**で見つかった、**設定の表示**のドロップダウン ボックス、**フォントおよび色**プロパティ ページ。  
  
 エディターを使用する場合は、特化したフォントと色の制御メカニズムを制御および拡張言語サービスを提供するを使用する必要があります、**テキスト エディター**設定します。 このメカニズムと呼ばれます*構文の色分け*を示し。  
  
-   フォントと色の表示項目を管理するための簡略化された手法です。  
  
     詳細については、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> および <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> を参照してください。  
  
-   適切に定義された、最適化された色付けのメカニズムです。  
  
     詳細については、「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>」を参照してください。  
  
-   両方の機能からの組み込み表示項目を使用して、**テキスト EditorCategory**これらを拡張するとします。  
  
     詳細については、次を参照してください。[する方法: 組み込みの装飾が可能な項目を使用して](../extensibility/internals/how-to-use-built-in-colorable-items.md)と[カスタムの装飾が可能なアイテム](../extensibility/internals/custom-colorable-items.md)です。  
  
-   組み込みの状態およびカスタムの現在の自動保持を持つ項目を表示する、**テキスト エディター**カテゴリ。  
  
 詳細については、構文の色分けを参照してください[レガシ言語サービスでの構文が色分け](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)です。  
  
## <a name="see-also"></a>参照  
 [エディターでの従来のインターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)   
 [従来の言語サービスでの構文の色分け表示](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)