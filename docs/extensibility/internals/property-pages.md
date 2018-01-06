---
title: "プロパティ ページ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cedf021321b66c47690450823a7da92cd19888eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="property-pages"></a>プロパティ ページ
ユーザーは、表示し、プロパティ ページを使用して、プロジェクトの構成に依存して、独立系のプロパティを変更できます。 A**プロパティ ページ**でボタンが有効になっている、**プロパティ**ウィンドウまたは 選択されたオブジェクトのプロパティ ページ ビューを提供するオブジェクトのソリューション エクスプ ローラー ツールバー。 プロパティ ページでは、環境によって作成され、ソリューションおよびプロジェクトに使用できます。 することができます、ただし、構成するプロジェクト項目を構成に依存するプロパティの使用の使用可能です。 プロジェクト内のファイルが別のコンパイラ スイッチの設定を正しくビルドする必要がある場合は、この機能を使用する場合があります。  
  
## <a name="using-property-pages"></a>プロパティ ページの使用  
 プロパティ ページがまだ表示されていると、選択範囲が (たとえば、ソリューションからプロジェクトに)、新しい選択範囲のプロパティを表示するページに表示される情報を変更します。 プロパティ ページをサポートするオブジェクトのプロパティがない場合、プロパティ ページが空です。  
  
 複数のオブジェクトが選択されている場合、プロパティ ページには、選択したすべてのアイテムのプロパティの共通部分が表示されます。 選択した項目に構成に依存するプロパティが含まれていないかどうか、**プロパティ ページ**ソリューション エクスプ ローラー ツールバーのボタンがクリックされると、[プロパティ] ウィンドウにフォーカスが変更されます。 詳細については、[プロパティ] ウィンドウと選択に関連する、次を参照してください。[の拡張プロパティ](../../extensibility/internals/extending-properties.md)です。  
  
 複数のオブジェクトのプロパティが表示されますが、プロパティ ページで値を変更すると、すべてのオブジェクトの値が設定されます、新しい値をでもが最初に異なると、個々 のオブジェクトのプロパティが表示されていたときに、ページが空白です。  
  
 2 つの一般的な種類があります**ProjectProperty ページ** ダイアログ ボックスで使用できる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 Visual Basic プロジェクトの場合、最初のなどのプロパティ ページは表示フィールドの形式を使用して次のスクリーン ショットに示すようにします。 1 秒間には、後でこのセクションで示した、プロパティ ページのホスト プロパティ グリッド プロパティ ウィンドウで確認するときと同様です。  
  
 ![Visual Basic プロパティ ページ](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
フィールドの形式とツリーの構造を持つプロジェクト プロパティ ページ ダイアログ ボックス  
  
 プロパティ ページ ダイアログ ボックスのツリー構造の使用が組み込まれていない<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>です。 によって渡されたレベル名に基づいて、環境、<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>インターフェイスを構築します。  
  
 使用できる 2 つの最上位のカテゴリが[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロパティ ページ。  
  
-   一般的なプロパティは、選択したオブジェクトまたはオブジェクトの構成に依存しない情報が表示されます。 その結果、共通プロパティのサブカテゴリのいずれかを選択すると、ダイアログ ボックスの一番上に、構成、プラットフォーム、および Configuration Manager のオプションは使用できません。  
  
-   ソリューションまたはプロジェクトのデバッグ、最適化、およびビルドのパラメーターに関連する構成に依存する情報を格納する構成プロパティされます。  
  
 その他の最上位のカテゴリを作成することはできませんの実装でどちらか一方を表示しないように選択して`IVsPropertyPage`です。 たとえば、オブジェクトを表示するすべての構成に依存しないプロパティがないの場合は、共通プロパティ カテゴリを表示しないように選択できます。 場合、共通のプロパティを表示する`ISpecifyPropertyPages`を実装する場合は、アイテムの参照オブジェクトと構成プロパティから実装`ISpecifyPropertyPages`構成オブジェクトに (実装するオブジェクト`IVsCfg`、 `IVsProjectCfg`、および関連します。インターフェイス)。  
  
 最上位のカテゴリの下に表示される各カテゴリは、個別のプロパティ ページを表します。 Category と subcategory 使用できるエントリ ダイアログ ボックスでは、実装によって決まります`ISpecifyPropertyPages`と`IVsPropertyPage`です。  
  
 `IDispatch`オブジェクトのプロパティ ページの実装に表示されるプロパティを持つ項目が選択コンテナーに`ISpecifyPropertyPages`クラス Id の一覧を列挙します。 変数として渡されるクラス Id`ISpecifyPropertyPages`プロパティ ページをインスタンス化に使用されます。 クラス Id のリストに渡されます`IVsPropertyPage` ダイアログ ボックスの左側のツリー構造を作成します。 バックアップを作成し、プロパティ ページ、パス情報、`IDispatch`を実装するオブジェクト`ISpecifyPropertyPages`し、各ページの情報を格納します。  
  
 使用して参照オブジェクトのプロパティを取得`IDispatch`選択コンテナー内の各オブジェクトです。  
  
 実装する`Help::DisplayTopicFromF1Keyword`VSPackage では、[ヘルプ] ボタンの機能を提供します。  
  
 詳細については、次を参照してください。`IDispatch`と`ISpecifyPropertyPages`、MSDN ライブラリです。  
  
 プロパティ ページの 2 番目の型に表示されますサンプル ホスト プロパティ グリッドのフォームの次のスクリーン ショットに示すようにします。  
  
 ![VC プロパティ ページ](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
プロパティ グリッドとプロパティ ページ ダイアログ ボックス  
  
 インターフェイス`IVSMDPropertyBrowser`と`IVSMDPropertyGrid`(vsmanaged.h で宣言) を作成し、ダイアログ ボックス内またはウィンドウ内で、プロパティ グリッドを設定するために使用します。  
  
 旧バージョンからプロジェクトのアーキテクチャが大幅に変更された[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 具体的には、プロジェクトの概念がアクティブなが変更されました。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、アクティブなプロジェクトの概念はありません。 以前の開発環境では、アクティブなプロジェクトを構築し、コマンドを配置するプロジェクトのコンテキストに関係なくを既定値はでした。 ここで、ソリューションが制御し、これをビルドおよびコマンドの配置を介し先となるプロジェクトに適用します。  
  
 構成していたアクティブなプロジェクトは、3 つの方法のいずれかで現在キャプチャされます。  
  
-   スタートアップ プロジェクト  
  
     以上のユーザーは、f5 キーを押すか、[ビルド] メニューから実行を選択したときに開始されるソリューションのプロパティ ページからプロジェクトを指定することができます。 これは、その名前が太字のフォントを持つソリューション エクスプ ローラーに表示されるという意味で古いアクティブなプロジェクトと同様の方法で機能します。  
  
     オートメーション モデルのプロパティとして、スタートアップ プロジェクトを取得するには呼び出すことによって`DTE.Solution.SolutionBuild.StartupProjects`です。 VSPackage でを呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>メソッドです。 `IVsSolutionBuildManager`サービスとして利用できます`QueryService`SID_SVsSolutionBuildManager にします。 詳細については、次を参照してください。[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)と[ソリューション構成](../../extensibility/internals/solution-configuration.md)です。  
  
-   アクティブなソリューションのビルド構成  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実装することで、オートメーション モデルで使用できるアクティブなソリューション構成を持つ`DTE.Solution.SolutionBuild.ActiveConfiguration`します。 ソリューション構成は、(各プロジェクトは複数の構成を複数の異なる名前を持つ、複数のプラットフォームでに持つことができます)、ソリューション内の各プロジェクトの 1 つのプロジェクト構成を含むコレクションです。 詳細については、ソリューションのプロパティ ページに関連する、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)です。  
  
-   現在選択されているプロジェクト  
  
     実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>プロジェクト階層やプロジェクト項目、選択された項目を取得します。 使用する DTE から、`SelectedItems.SelectedItem.Project`と`SelectedItems.SelectedItem.ProjectItem`メソッドです。 コアにそれらの見出しの下のサンプル コードがある[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ドキュメント。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)   
 [プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)