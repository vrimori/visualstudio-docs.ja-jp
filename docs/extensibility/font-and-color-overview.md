---
title: "フォントと色の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK]、[フォントおよび色"
  - "フォントおよびカラー コントロール [Visual Studio SDK] エディター"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# フォントと色の概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境でテキストのフォントおよび色の設定について説明します \(IDE\)。  またカテゴリおよび表示項目の概念や VSPackage とコア エディターでテキスト属性を使用する方法について説明します。  
  
## フォントおよび色のプロパティ ページ  
 \[入力\] プロパティ ENT0ENT なページから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境に表示 \(IDE\) されるテキストの属性を管理できます。  \[入力\] プロパティ ページを ENT0ENT な ENT1ENT\[入力\] メニューの ENT2ENT\[検索\] をクリックします。  **\[環境\]** を展開して、**\[フォントおよび色\]** をクリックします。  
  
## カテゴリおよび表示項目  
 フォントや色が  **カテゴリ**  と  **表示項目**  に編成されます。  
  
-   **カテゴリ**  は多数の  **表示項目**  の論理機能またはコンテナーです。  
  
     **カテゴリ**  の一覧が ENT2ENT \[入力\] プロパティのページの \[ENT1ENT\] のドロップダウン ボックスにあります。  
  
-   **\*\*\* Display Item \*\*\*** コメントはStringまたは colorized 制御構造など明示されているテキストのエンティティが表示されます。  
  
 各 **\*\*\* Display Item \*\*\*** は  **カテゴリ**  内で識別します。が含まれています。  したがって複数の  **カテゴリ**  は同じ名前の **\*\*\* Display Item \*\*\*** を持つことができます。  
  
## フォントおよび色の VSPackage のコントロール  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 許可の VSPackages に :  
  
-   フォントを定義し **カテゴリ**  の色指定します。  
  
-   **表示項目**  の表示に使用されるフォントと色を指定します。  
  
-   \[入力\] プロパティ ENT0ENT なページとやり取りします。  
  
-   グループの集計に複数の  **カテゴリ** 。  
  
-   既定の設定は変更が保持されます。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 内のフォントと色を選択すると対話する方法が 2 つあります。  
  
-   1 番目の方法は *構文の色指定*  と呼ばれます。  これは言語サービスを実行しソース エディターを作成するに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の既存のエディターをカスタマイズする VSPackage で使用されます。  
  
     1  **カテゴリ**  のみこの機能つまり **テキスト エディター**  をサポートします。  
  
-   一般的な方法はソース エディターのテキストを表示する場合に他の  **カテゴリ**  とユーザー インターフェイス コンポーネントがすべてサポートします。  詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>」を参照してください。  
  
## コア エディターのテキストの設定  
 言語サービスのオブジェクトのコア エディターのフォントおよび色の設定は\[プロパティ\] ENT3ENT なページ ENT2ENT \[入力\] のドロップダウン ボックスの \[ **テキスト エディター  カテゴリ**  によって管理されます。  
  
 エディターを使用する場合は特殊なフォントを使用して **テキスト エディター**  設定を制御し拡張する言語サービスを提供する特別なコントロールに色を付ける必要があります。  機能は  *構文の色指定*  と呼ばれますされています :  
  
-   表示項目の色とフォントを管理するための簡単な方法。  
  
     詳細については、「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>」および「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>」を参照してください。  
  
-   正しく定義され最適化された色づけ機能。  
  
     詳細については、「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>」を参照してください。  
  
-   **テキスト エディター   カテゴリ**  の両方で使用する組み込みの項目を表示する機能とそれらを拡張します。  
  
     詳細については、「[方法: ビルトインの装飾が可能な項目を使用して](../extensibility/internals/how-to-use-built-in-colorable-items.md)」および「[カスタムの装飾が可能な項目](../extensibility/internals/custom-colorable-items.md)」を参照してください。  
  
-   **テキスト エディター**  カテゴリの組み込みレポートおよびカスタムの表示項目の現在の状態を自動永続化されます。  
  
 構文の色指定の詳細に [構文の色分けで従来の言語サービス](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md) を参照してください。  
  
## 参照  
 [エディターでのレガシー インターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)   
 [構文の色分けで従来の言語サービス](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)